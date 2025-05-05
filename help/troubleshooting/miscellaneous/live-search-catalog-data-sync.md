---
title: Katalogen för Live-sökning är inte synkroniserad
description: Den här artikeln innehåller lösningar på Adobe Commerce-problemet där katalogdata inte synkroniseras korrekt när du använder tillägget Live Search.
exl-id: cd2e602f-b2c7-4ecf-874f-ec5f99ae1900
feature: Catalog Management, Search
role: Developer
source-git-commit: fec99ebd6b03f2dc1b70c0ea388935dc5e60ad57
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 0%

---

# Katalogen för Live-sökning är inte synkroniserad

Den här artikeln innehåller lösningar på Adobe Commerce-problemet där katalogdata inte synkroniseras korrekt när du använder tillägget Live Search.

## Berörda produkter och versioner

* Adobe Commerce 2.4.x med Live Search-tillägg installerat

## Problem

Katalogdata är inte korrekt synkroniserade eller så har en ny produkt lagts till, men visas inte i sökresultaten. Du kan även få följande fel i `var/log/exception.log`:

`Magento_LiveSearch: An error occurred in search backend. {"result":{"errors":[{"message":"Exception while fetching data (/productSearch) : No index was found for this request"}]}}`

>[!NOTE]
>
>Tabellnamnen `catalog_data_exporter_products` och `catalog_data_exporter_product_attributes` kallas nu `cde_products_feed` och `cde_product_attributes_feed` från och med [!DNL Live Search] version 4.2.1. För handlare med versioner före 4.2.1, sök efter data i de gamla tabellnamnen, `catalog_data_exporter_products` och `catalog_data_exporter_product_attributes`.

<u>Steg som ska återskapas</u>

1. Konfigurera och anslut Live Search för din Adobe Commerce-instans enligt beskrivningen i [Installera Live Search > Konfigurera API-nycklar](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=sv-SE#configure-api-keys) i användardokumentationen.
1. Efter 30 minuter kontrollerar du de exporterade katalogdata som beskrivs i [Installera Live Search > Verifiera export](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=sv-SE#verify-export) i användardokumentationen.
1. Efter 30 minuter testar du anslutningen enligt beskrivningen i [Installera Live Search > Testa anslutningen](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=sv-SE#test-connection) i användardokumentationen.

eller

1. Lägg till en ny produkt i katalogen.
1. Försök att köra en sökfråga med produktnamnet eller andra sökbara attribut efter 15-20 minuter från det att Magento indexer + cron har körts för att synkronisera data till serverdelstjänsten.

<u>Förväntat resultat</u>

* Exporterade katalogdata kan verifieras
* Anslutningen lyckades
* Ny produkt visas i sökresultaten.

<u>Faktiskt resultat</u>

Det går inte att verifiera den exporterade katalogen och/eller anslutningen har inte upprättats eftersom API-nyckeln har ändrats.

## Lösning

Det finns flera saker du kan göra för att försöka åtgärda problemet med katalogsynkronisering.

### Vänta på att ändringarna ska tillämpas

När du har konfigurerat och anslutit kan det ta över 30 minuter innan indexet i ES (Elasticsearch) skapas och sökresultaten returneras. Efterföljande engångsuppdateringar förväntas indexeras inom några minuter.

### Synkronisera produktdata för en specifik SKU

Om dina produktdata inte synkroniseras korrekt för en viss SKU gör du följande:

1. Använd följande [!DNL SQL]-fråga och verifiera att du har de data du förväntar dig i kolumnen `feed_data`. Notera också tidsstämpeln `modified_at`.

   ```sql
   SELECT * FROM cde_products_feed WHERE json_extract(feed_data, '$.sku') = '<your_sku>' AND json_extract(feed_data, '$.storeViewCode') = '<your_ store_view_code>';
   ```

   Exempel:

   ```sql
   SELECT * FROM cde_products_feed WHERE json_extract(feed_data, '$.sku') = '24-MB04' AND json_extract(feed_data, '$.storeViewCode') = 'default';
   ```

1. Om du inte ser rätt data kan du försöka indexera om med följande kommando och köra [!DNL SQL]-frågan igen i steg 1 för att verifiera data:

   ```bash
   bin/magento indexer:reindex cde_products_feed
   ```

1. Om du fortfarande inte ser rätt data [skapar du en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Kontrollera tidsstämpel för senaste produktexport

1. Om du ser rätt data i `cde_products_feed` använder du följande [!DNL SQL]-fråga för att kontrollera tidsstämpeln för den senaste exporten. Det ska vara efter tidsstämpeln `modified_at`:

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. Om tidsstämpeln är äldre kan du antingen vänta på nästa kron-körning eller utlösa den själv med följande kommando:

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Vänta i `<>` tid (tid för inkrementella uppdateringar). Om du fortfarande inte ser dina data [skapar du en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Synkronisera specifik attributkod

Om produktattributdata inte synkroniseras korrekt för en viss attributkod gör du följande:

1. Använd följande [!DNL SQL]-fråga och verifiera att du har de data du förväntar dig i kolumnen `feed_data`. Notera också tidsstämpeln `modified_at`.

   ```sql
   select * from cde_product_attributes_feed where json_extract(feed_data, '$.attributeCode') = '<your_attribute_code>' and store_view_code = '<your_ store_view_code>';
   ```

1. Om du inte ser rätt data använder du följande kommando för att indexera om och kör sedan [!DNL SQL]-frågan igen i steg 1 för att verifiera data.

   ```bash
   bin/magento indexer:reindex cde_product_attributes_feed
   ```

1. Om du fortfarande inte ser rätt data [skapar du en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Kontrollera tidsstämpel för export av senaste produktattribut

Om du ser rätt data i `cde_product_attributes_feed`:

1. Använd följande [!DNL SQL]-fråga för att kontrollera tidsstämpeln för den senaste exporten. Det ska vara efter tidsstämpeln `modified_at`.

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. Om tidsstämpeln är äldre kan du antingen vänta på nästa kron-körning eller utlösa den själv med följande kommando:

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Vänta i 15-20 minuter (tid för stegvisa uppdateringar). Om du fortfarande inte ser dina data kan du [skapa en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Synkronisera efter ändring av API-konfiguration

(Känt fel) Om du har ändrat din API-konfiguration, vilket leder till en ändring av ditt Data Space-ID och upptäcker att katalogändringarna inte längre synkroniseras, kör du följande kommandon för att synkronisera om flödena:

```
bin/magento saas:resync --feed productattributes --cleanup-feed
bin/magento saas:resync --feed products --cleanup-feed
bin/magento saas:resync --feed scopesCustomerGroup --cleanup-feed
bin/magento saas:resync --feed scopesWebsite --cleanup-feed
bin/magento saas:resync --feed prices --cleanup-feed
bin/magento saas:resync --feed productOverrides --cleanup-feed
bin/magento saas:resync --feed variants --cleanup-feed
bin/magento saas:resync --feed categories --cleanup-feed
bin/magento saas:resync --feed categoryPermissions --cleanup-feed
```

[Skicka en supportförfrågan](https://experienceleague.adobe.com/home?lang=sv-SE&support-tab=home#support) om du vill begära omindexering av Live Search-indexet. I felbeskrivningen tar du med ditt ID för datautrymme/miljö som finns på administratörspanelen under **[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Commerce Services Connector]**.

>[!IMPORTANT]
>Använd bara alternativet `--cleanup-feed` om du har uppdaterat API-konfigurationen, eller om du kör kommandot `saas:resync` med alternativet [ - torr](https://experienceleague.adobe.com/sv/docs/commerce/saas-data-export/data-export-cli-commands#--dry-run). Om du använder alternativet `--cleanup-feed` i andra fall uppstår problem med förlorade data och datasynkronisering.

## Relaterad läsning

* [Onboard Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/onboarding-overview.html?lang=sv-SE) i vår användardokumentation
* [Granska loggar och felsöka dataexport och synkronisering i Adobe Commerce SaaS](https://experienceleague.adobe.com/sv/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging) i Adobe Commerce SaaS dataexportguide
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
