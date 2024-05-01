---
title: 'ACSD-53925: Det går inte att spara CMS-block med [!UICONTROL Product Carousel]'
description: Använd patchen ACSD-53925 för att åtgärda Adobe Commerce-problemet där administratören inte kan spara ett CMS-block med Product Carousel när dimensionsläget för "catalog_product_price" är inställt på webbplatsen.
feature: CMS, Page Builder, Price Indexer, Products
role: Admin, Developer
exl-id: 6ef6d8ff-4ebb-4adb-9fb7-0d4a81a25f50
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-53925: Det går inte att spara CMS-block med *[!UICONTROL Product Carousel]*

Korrigeringen ACSD-53925 åtgärdar ett problem där administratören inte kan spara ett CMS-block med *[!UICONTROL Product Carousel]* när dimensionsläge för `catalog_product_price` är inställt på webbplats. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.43 är installerat. Korrigerings-ID är ACSD-53925. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratören kan inte spara ett CMS-block med *[!UICONTROL Product Carousel]* när dimensionsläge för `catalog_product_price` är inställt på webbplats.

<u>Steg som ska återskapas</u>:

1. Skapa två enkla produkter:
   * simple1 - $10
   * simple2 - $20
1. Skapa en paketprodukt &#39;*bundle1-dyn*&quot; med två alternativ som bygger på enkla produkt-SKU:er.
1. Ange dimensionsläge för produktprisindexeraren:

   `bin/magento indexer:set-dimensions-mode catalog_product_price website`

1. Gå till **[!UICONTROL Content]** > **[!UICONTROL Blocks]** och skapa ett nytt CMS-block.
1. Redigera innehåll med [!DNL Page Builder]:
   * Lägg till en *[!UICONTROL Row]* element
   * Lägg till en *[!UICONTROL Products]* element
   * Välj *[!UICONTROL Product Carousel]*
   * Ange produkt-SKU *bundle1-dyn*
1. Spara CMS-blocket.

<u>Förväntade resultat</u>:

Användaren kan lägga till en produktCarousel utan fel.

<u>Faktiska resultat</u>:

* Ett meddelande visas i användargränssnittet: *Ett fel uppstod när innehållet genererades*
* `var/log/exception.log` innehåller följande fel:

  ```
  [2023-08-18T20:58:14.533374+00:00] report.CRITICAL: PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'username_dev.catalog_product_index_price_ws0' doesn't exist in /test/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
  ```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
