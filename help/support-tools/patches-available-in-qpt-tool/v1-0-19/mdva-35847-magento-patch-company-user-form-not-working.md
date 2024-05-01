---
title: 'MDVA-35847: Företagets användarformulär fungerar inte'
description: MDVA-35847-korrigeringen löser problemet med att företagsanvändarformuläret inte fungerar och returnerar ett 500-fel på framsidan. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Patch-ID:t är MDVA-35847. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.
exl-id: 1a3f4a61-0c21-460a-ae48-e792d03ed805
feature: B2B, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# MDVA-35847: Företagets användarformulär fungerar inte

MDVA-35847-korrigeringen löser problemet med att företagsanvändarformuläret inte fungerar och returnerar ett 500-fel på framsidan. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Patch-ID:t är MDVA-35847. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce i molninfrastruktur 2.4.2

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.4.1-2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Förutsättningar</u>:

Adobe Commerce B2B är installerat.

<u>Steg som ska återskapas</u>:

1. Gå till **Lager** > **Attribut** > **Kund** och skapa ett nytt kundattribut:

   * Indatatyp = *Datum*
   * Visa på Storefront = *Ja*
   * Sorteringsordning = *0*
   * Forms to Use In = *Alla formulär*

1. Skapa ett nytt företag.
1. Logga in som företagsadministratör i början.
1. Gå till avsnittet Företagsanvändare.

<u>Förväntade resultat</u>:

Företagets användarformulär läses in normalt.

<u>Faktiska resultat</u>:

Företagets användarformulär läses inte in och returnerar ett 500-fel.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
