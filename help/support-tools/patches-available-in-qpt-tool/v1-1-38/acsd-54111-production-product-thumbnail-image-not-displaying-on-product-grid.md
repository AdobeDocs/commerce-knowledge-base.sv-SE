---
title: 'ACSD-54111: Produktminiatyrbilden visas inte'
description: Använd korrigeringsfilen ACSD-54111 för att åtgärda Adobe Commerce-problemet där alla bilder ersätts av standardproduktplatshållarbilden.
feature: Products
role: Admin, Developer
exl-id: 087786e3-9d61-4fef-8884-8d22fa9170e3
source-git-commit: a863015920917050106ed5d210d0511515807cc7
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-5411: Miniatyrbilden av produkten visas inte

Korrigeringen ACSD-5411 åtgärdar ett problem där alla bilder ersätts av standardproduktplatshållarbilden. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 är installerat. Korrigerings-ID är ACSD-5411. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder): 2.4.5-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder): 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktminiatyrbilden visas inte.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]** > **[!UICONTROL Edit Theme]** > **[!UICONTROL Product Image Watermarks]** > **[!UICONTROL Thumbnail]**.
1. Överför bilden med en miniatyrbild och ange bildpositionen som *[!UICONTROL Center]*.
1. Klicka på **[!UICONTROL Save Configuration]**.
1. Rensa cache.
1. Gå till butiken som gäst/kund.
1. Lägg en produkt i kundvagnen.
1. Kör `bin/magento catalog:image:resize` från konsolen.
1. Öppna miniatyrbilden på framänden eller produktrutnätet på bakänden för att se om miniatyrbilderna är synliga.

<u>Förväntade resultat</u>:

Produktbilder ersätts inte med platshållarbilden.

<u>Faktiska resultat</u>:

Produktbilder ersätts med standardbilden för produktplatshållaren.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
