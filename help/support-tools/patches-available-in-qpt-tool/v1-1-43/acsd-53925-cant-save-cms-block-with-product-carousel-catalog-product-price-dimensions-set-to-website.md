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

Korrigeringen ACSD-53925 åtgärdar ett problem där administratören inte kan spara ett CMS-block med *[!UICONTROL Product Carousel]* när dimensionsläget för `catalog_product_price` är inställt på webbplatsen. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.43 har installerats. Korrigerings-ID är ACSD-53925. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratören kan inte spara ett CMS-block med *[!UICONTROL Product Carousel]* när dimensionsläget för `catalog_product_price` är inställt på webbplatsen.

<u>Steg som ska återskapas</u>:

1. Skapa två enkla produkter:
   * simple1 - $10
   * simple2 - $20
1. Skapa en paketprodukt *bundle1-dyn* med två alternativ som baseras på enkla produkt-SKU:er.
1. Ange dimensionsläge för produktprisindexeraren:

   `bin/magento indexer:set-dimensions-mode catalog_product_price website`

1. Gå till **[!UICONTROL Content]** > **[!UICONTROL Blocks]** och skapa ett nytt CMS-block.
1. Redigera innehållet med [!DNL Page Builder]:
   * Lägg till ett *[!UICONTROL Row]*-element
   * Lägg till ett *[!UICONTROL Products]*-element
   * Välj *[!UICONTROL Product Carousel]*
   * Ange produkt-SKU - *bundle1-dyn*
1. Spara CMS-blocket.

<u>Förväntade resultat</u>:

Användaren kan lägga till en produktCarousel utan fel.

<u>Faktiska resultat</u>:

* Ett meddelande genereras i användargränssnittet: *Ett fel uppstod när innehållet genererades*
* `var/log/exception.log` innehåller följande fel:

  ```
  [2023-08-18T20:58:14.533374+00:00] report.CRITICAL: PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'username_dev.catalog_product_index_price_ws0' doesn't exist in /test/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
  ```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
