---
title: 'ACSD-47054: Förhandsgranska innehåll långsamt när alla butiker indexerar om'
description: Använd korrigeringsfilen ACSD-47054 för att åtgärda Adobe Commerce-problemet där förhandsvisningssidan laddas långsamt på grund av omindexering av alla butiker.
feature: Page Content
role: Admin, Developer
exl-id: 4dc61f78-7038-48ab-a2d3-9b05cf0c9b5c
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-47054: Förhandsgranska innehåll långsamt när alla butiker indexerar om

Korrigeringen ACSD-47054 åtgärdar ett problem där en förhandsgranskning av innehållstagningen tar längre tid att läsa in när det finns många butiker. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.37 är installerat. Korrigerings-ID är ACSD-47054. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder): 2.4.2-p2, 2.4.5-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder): 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det tar lång tid att läsa in förhandsgranskningssidan eftersom alla butiker har indexerats om.

<u>Steg som ska återskapas</u>:

1. Gå till Commerce Admin.
1. Skapa schemalagda uppdateringar.
1. Gå till **[!UICONTROL Content]** > **[!UICONTROL Dashboard]**.
1. Förhandsgranska den schemalagda uppdateringen.
1. Öppna en kategori.

<u>Förväntade resultat</u>:

Förhandsgranskningssidan läses in inom en acceptabel tidsperiod.

<u>Faktiska resultat</u>:

Det tar lång tid att förhandsgranska innehållstagningen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
