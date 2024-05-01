---
title: 'MDVA-44940: SQL-fel när kategori sparas från admin'
description: MDVA-44940-korrigeringen åtgärdar ett problem där ett SQL-fel inträffar när en kategori sparas från administratören. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 är installerat. Korrigerings-ID är MDVA-44940. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
exl-id: cae6f231-3b91-441f-af56-824db0fa2d32
feature: Admin Workspace, Categories, Sales Channels
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-44940: SQL-fel när kategori sparas från admin

MDVA-44940-korrigeringen åtgärdar ett problem där ett SQL-fel inträffar när en kategori sparas från administratören. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 är installerat. Korrigerings-ID är MDVA-44940. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett SQL-fel inträffar när en kategori sparas från administratören.

<u>Steg som ska återskapas</u>:

1. Installera exempeldata.
1. Skapa en andra webbplats med en butiksgrupp tilldelad standardkategorin.

   * Skapa en butiksvy som tilldelats den nya butiksgruppen.

1. Skapa Stock och ytterligare en källa som är tilldelad detta lager och en försäljningskanal som är tilldelad den andra webbplatsen.
1. Skapa en testprodukt som tilldelats den andra webbplatsen.
1. Gå till **Administratör** > **Katalog** > **Kategorier**, markera **Omfång** = **Andra webbplatsen** och gå till **Produkter i kategori** > **Automatisk sortering** > Flytta färdiga produkter längst ned och klicka **Spara**.

<u>Förväntade resultat</u>:

Kategorin sparas.

<u>Faktiska resultat</u>:

Följande fel inträffar: *Något gick fel när kategorin sparades*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
