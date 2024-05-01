---
title: 'MDVA-36286: Page Builder-förhandsvisningen avbryts om SKU-positionerna i olika kategorier bryts.'
description: MDVA-36286-korrigeringen löser problemet där förhandsvisningen av Page Builder-produktwidgeten bryts om samma SKU har en annan position i underkategorier. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.23 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.
exl-id: 0f7d2506-569a-4b70-82bf-0f153014c48a
feature: CMS, Categories, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# MDVA-36286: Page Builder-förhandsvisning avbryts om SKU-positionerna i olika kategorier bryts

MDVA-36286-korrigeringen löser problemet där förhandsvisningen av Page Builder-produktwidgeten bryts om samma SKU har en annan position i underkategorier. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.23 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce om molninfrastruktur 2.3.6

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.3.6 - 2.4.2-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas:</u>

1. Skapa en kategori med några produkter.
   ![products_magento_ordered.png](/help/support-tools/patches-available-in-qpt-tool/assets/products_magento_ordered.png)
1. Skapa en underkategori med samma produkter men med olika positioner.
   ![products_magento_different_position.png](/help/support-tools/patches-available-in-qpt-tool/assets/products_magento_different_position.png)
1. Redigera innehåll på en CMS-sida och lägg till en produktwidget via Page Builder. (Välj den överordnade kategorin ovan).
   ![cms_page_magento.png](/help/support-tools/patches-available-in-qpt-tool/assets/cms_page_magento.png)
1. Spara och vänta på förhandsgranskningen av innehållet.

<u>Förväntade resultat:</u>

Förhandsgranska innehåll visar produktwidgeten.

<u>Faktiska resultat:</u>

Fel som visas:

*Ett fel uppstod när det här innehållet genererades.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
