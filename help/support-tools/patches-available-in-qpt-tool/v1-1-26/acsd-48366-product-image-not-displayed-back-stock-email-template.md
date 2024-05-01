---
title: '''ACSD-48366: produktbild visas inte på [!UICONTROL Back to Stock] e-postmall'
description: Använd patchen ACSD-48366 för att åtgärda problemet med Adobe Commerce där miniatyrbilden av produkten inte visas i produktens varningsmeddelande.
exl-id: 57b549b0-6e97-4d5f-927e-9585f3257872
feature: Admin Workspace, Communications, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-48366: produktbild visas inte på [!UICONTROL Back to Stock] e-postmall

Korrigeringen ACSD-48366 åtgärdar ett problem där produktminiatyrbilden inte visas i produktens varningsmeddelande. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 är installerat. Korrigerings-ID är ACSD-48366. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktbilden visas inte på [!UICONTROL Back to Stock] e-postmall.

<u>Steg som ska återskapas</u>:

1. Aktivera *[!UICONTROL Product Alert]* for *[!UICONTROL Back in Stock]* genom att **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]** > **[!UICONTROL Allow Alert When Product Comes Back in Stock]** = *[!UICONTROL Yes]*.
1. Aktivera *[!UICONTROL Display Out of Stock Products]* genom att **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Display Out of Stock]** = *[!UICONTROL Yes]*.
1. Skapa en enkel produkt med kvantitet = 0.
1. Skapa en kund från butiken och prenumerera på produkten ovan för att få produktvarningar när den finns i lager.
1. Gör produkten i lager.
1. Kör produktvarningsprogrammet.

   ```
   n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Starta produktvarningen för kunden.

   ```
   bin/magento queue:consumers:start product_alert
   ```

1. Kontrollera e-postmeddelandet. Lagervarningsmeddelanden ska nu vara tillgängliga i e-postkatalogen.

<u>Förväntade resultat</u>:

Produktbilden visas i e-postmeddelandet om stockmeddelanden.

<u>Faktiska resultat</u>:

Produktbilden är inte tillgänglig i e-postmeddelandet om lagermeddelanden.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
