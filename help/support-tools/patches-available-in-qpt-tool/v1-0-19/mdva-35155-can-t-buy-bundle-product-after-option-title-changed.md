---
title: "MDVA-35155: Det går inte att köpa paketprodukten när alternativtiteln har ändrats"
description: MDVA-35155-korrigeringen löser problemet där en paketprodukt inte kan köpas efter att alternativtiteln har ändrats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Patch-ID:t är MDVA-35155. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.
exl-id: 79770c69-1bb0-48d8-acdf-c8c1272f9da8
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-35155: Det går inte att köpa paketprodukten när alternativtiteln har ändrats

MDVA-35155-korrigeringen löser problemet där en paketprodukt inte kan köpas efter att alternativtiteln har ändrats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Patch-ID:t är MDVA-35155. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce om molninfrastruktur 2.3.5

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.0-2.3.5-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Paketprodukter kan inte köpas efter att alternativtiteln har ändrats.

<u>Steg som ska återskapas</u>:

1. Skapa en ny paketprodukt via **Produktimport**.
1. Produkten är normal både i Admin och i klientledet (i lager och kan läggas till i kundvagnen).
1. Uppdatera samma produkt med ändringar i namnet i `bundle_values` och importera produkten igen.

<u>Förväntade resultat</u>:

Det befintliga paketalternativet uppdateras till det nya namnet och behåller samma objekt.

<u>Faktiska resultat</u>:

* Administratören försöker sammanfoga produkter med samma SKU i en enda paketalternativsektion, vilket resulterar i en tom alternativsektion.
* Produkten finns inte i lager vid frontend (även efter omindexering).

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
