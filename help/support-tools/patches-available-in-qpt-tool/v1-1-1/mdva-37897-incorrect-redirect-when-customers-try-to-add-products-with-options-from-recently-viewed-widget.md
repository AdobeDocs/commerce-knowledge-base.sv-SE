---
title: 'MDVA-37897: Felaktig omdirigering när du lägger till produkter från Senast visade'
description: MDVA-37897-korrigeringen löser problemet med felaktig omdirigering när användare försöker lägga till produkter med alternativ från widgeten Senast visade. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 är installerat. Patch-ID:t är MDVA-37897. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.4.
exl-id: f0a86e02-b357-4d2d-8386-e9cc045bcf06
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-37897: Felaktig omdirigering när produkter från Senast visade läggs till

MDVA-37897-korrigeringen löser problemet med felaktig omdirigering när användare försöker lägga till produkter med alternativ från widgeten Senast visade. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 är installerat. Patch-ID:t är MDVA-37897. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce i vår molninfrastruktur 2.4.1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När en användare försöker lägga till en produkt från avsnittet Senast visade som kräver att du väljer alternativ, dirigeras användaren till produktlistsidan i stället för till produktinformationssidan.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt med anpassningsbara alternativ (Typ: Alternativknapp).
1. Konfigurera widgeten Senast visade om du vill visa produkter.
1. Besök produkter som har anpassningsbara alternativ så att de visas i widgeten Senast visade.
1. Klicka **Lägg i kundvagnen** på en av produkterna i widgeten Senast visade.

<u>Förväntade resultat</u>:

Du omdirigeras till sidan med produktinformation för att välja alternativ.

<u>Faktiska resultat</u>:

Du omdirigeras till produktlistsidan.

## Tillämpa korrigeringen

Använd följande länkar beroende på vilken distributionstyp du har när du vill använda enskilda korrigeringsfiler:

* Adobe Commerce lokalt: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce i vår molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om kvalitetspatchar för Adobe Commerce finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
