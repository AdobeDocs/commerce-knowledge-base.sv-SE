---
title: 'ACSD-53098: Produkter i delad katalog återspeglar inte frontend'
description: Använd korrigeringsfilen ACSD-53098 för att åtgärda Adobe Commerce-problemet där produkter som tilldelats en delad katalog inte reflekteras på klientsidan när ett partiellt index körs.
feature: B2B, Catalog Management, Categories, Products
role: Admin, Developer
exl-id: 19c66a3a-04b2-48ee-aff3-ad2b592ff876
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-53098: Produkter i delad katalog återspeglar inte frontend

Korrigeringen ACSD-53098 åtgärdar ett problem där produkter som tilldelats till en delad katalog inte återspeglas i frontend när ett partiellt index körs. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.38 är installerat. Korrigerings-ID är ACSD-53098. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produkter som tilldelats en delad katalog via API visas inte i klientprogrammet efter att den partiella indexeraren har utfört kron-jobbet, följt av konsumentkron.

<u>Steg som ska återskapas</u>:

1. Konfigurera [!DNL RabbitMQ] som kötjänst.
1. Växla indexerare till **[!UICONTROL Update on Schedule]** läge.
1. Skapa en delad katalog och tilldela den till ett företag.
1. Skapa en enkel produkt och tilldela den till en kategori. Kör partiell omindexering:

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. Använd följande API-begäran för att tilldela den skapade produkten till den delade katalogen.

   ```
   pub/rest/all/V1/sharedCatalog/<id>/assignProducts
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. Kör följande kron för att rensa köerna och köra partiell omindexering:

   `bin/magento cron:run --group=consumers`

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. Logga in på frontend som företagets användare.
1. Kontrollera kategorisidan för frontend.

<u>Förväntade resultat</u>:

De nytilldelade produkterna visas i förgrunden.

<u>Faktiska resultat</u>:

De nyligen tilldelade produkterna visas inte i förgrunden.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
