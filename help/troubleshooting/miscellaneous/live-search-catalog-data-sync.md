---
title: Katalogen för Live-sökning är inte synkroniserad
description: Den här artikeln innehåller lösningar på Adobe Commerce-problemet där katalogdata inte synkroniseras korrekt när du använder tillägget Live Search.
exl-id: cd2e602f-b2c7-4ecf-874f-ec5f99ae1900
feature: Catalog Management, Search
role: Developer
source-git-commit: a1b049dab989d5d8594d86b64b778e6e277a9f41
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 0%

---

# Katalogen för Live-sökning är inte synkroniserad

Den här artikeln innehåller lösningar på Adobe Commerce-problemet där katalogdata inte synkroniseras korrekt när du använder tillägget Live Search.

## Berörda produkter och versioner

* Adobe Commerce 2.4.x med Live Search-tillägg installerat

## Problem

Katalogdata är inte korrekt synkroniserade eller så har en ny produkt lagts till, men visas inte i sökresultaten.

<u>Steg som ska återskapas</u>

1. Konfigurera och ansluta Live Search för din Adobe Commerce-instans enligt beskrivningen i [Installera Live Search > Konfigurera API-nycklar](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#configure-api-keys) i vår användardokumentation.
1. Efter 30 minuter kontrollerar du den exporterade kataloginformationen enligt beskrivningen i [Installera Live Search > Verifiera export](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#verify-export) i vår användardokumentation.
1. Efter 30 minuter testar du anslutningen enligt beskrivningen i [Installera Live Search > Testa anslutningen](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#test-connection) i vår användardokumentation.

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

1. Använd följande SQL-fråga och verifiera att du har de data du förväntar dig i `feed_data` kolumn. Anteckna också `modified_at` tidsstämpel.

   ```sql
   select * from catalog_data_exporter_products where sku = '<your_sku>' and store_view_code = '<your_ store_view_code>';
   ```

1. Om du inte ser rätt data kan du försöka indexera om med följande kommando och köra SQL-frågan igen i steg 1 för att verifiera data:

   ```bash
   bin/magento indexer:reindex catalog_data_exporter_products
   ```

1. Om du fortfarande inte ser rätt data, [skapa en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Kontrollera tidsstämpel för senaste produktexport

1. Om du ser rätt data i `catalog_data_exporter_products`använder du följande SQL-fråga för att kontrollera tidsstämpeln för den senaste exporten. Det ska vara efter `modified_at` tidsstämpel:

   ```sql
   select * from flag where flag_code = 'products-feed-version';
   ```

1. Om tidsstämpeln är äldre kan du antingen vänta på nästa kron-körning eller utlösa den själv med följande kommando:

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Vänta på `<>` tid (tid för stegvisa uppdateringar). Om du fortfarande inte ser dina data, [skapa en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Synkronisera specifik attributkod

Om produktattributdata inte synkroniseras korrekt för en viss attributkod gör du följande:

1. Använd följande SQL-fråga och verifiera att du har de data du förväntar dig i `feed_data` kolumn. Anteckna också `modified_at` tidsstämpel.

   ```sql
   select * from catalog_data_exporter_product_attributes where json_extract(feed_data, '$.attributeCode') = '<your_attribute_code>' and store_view_code = '<your_ store_view_code>';
   ```

1. Om du inte ser rätt data använder du följande kommando för att indexera om och kör sedan SQL-frågan igen i steg 1 för att verifiera data.

   ```bash
   bin/magento indexer:reindex catalog_data_exporter_product_attributes
   ```

1. Om du fortfarande inte ser rätt data, [skapa en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Kontrollera tidsstämpel för export av senaste produktattribut

Om du ser rätt data i `catalog_data_exporter_product_attributes`:

1. Använd följande SQL-fråga för att kontrollera tidsstämpeln för den senaste exporten. Det ska vara efter `modified_at` tidsstämpel.

   ```sql
   select * from flag where flag_code = 'product-attributes-feed-version';
   ```

1. Om tidsstämpeln är äldre kan du antingen vänta på nästa kron-körning eller utlösa den själv med följande kommando:

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Vänta i 15-20 minuter (tid för stegvisa uppdateringar). Om du fortfarande inte ser dina data, vänligen [skapa en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Synkronisera efter ändring av API-konfiguration

(Känt fel) Om du har ändrat din API-konfiguration, vilket leder till en ändring av ditt Data Space-ID och upptäcker att katalogändringarna inte längre synkroniseras, kör du följande kommandon:

```bash
bin/magento saas:resync --feed products
bin/magento saas:resync --feed productattributes
```

## Relaterad läsning

Se [Inbyggd Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/onboarding-overview.html) i vår användardokumentation.
