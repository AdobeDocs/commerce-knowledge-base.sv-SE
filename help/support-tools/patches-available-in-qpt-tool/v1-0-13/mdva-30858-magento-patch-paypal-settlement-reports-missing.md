---
title: 'MDVA-30858: Rapporter om PayPal-kvittning saknas'
description: "Korrigeringen MDVA-30858 korrigerar PayPal-kvittningsrapporter som saknas när det finns flera PayPal-konton. Rapporterna ska vara tillgängliga under administratörssidofältet &gt; **Reports** &gt; Sales &gt; **PayPal settlement**. I stället meddelandet: *Det gick inte att hitta några poster.* visas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 är installerat. Observera att problemet löstes i Adobe Commerce 2.4.2."
exl-id: 268aa74c-5cb5-4653-a6c9-1d4c30167e6a
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# MDVA-30858: Rapporter om PayPal-kvittning saknas

Korrigeringen MDVA-30858 korrigerar PayPal-kvittningsrapporter som saknas när det finns flera PayPal-konton. Rapporterna ska vara tillgängliga under administratörens sidopanel > **Rapporter** > Försäljning > **PayPal-kvittning**. I stället visas meddelandet: *Vi kunde inte hitta några poster.* visas. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce i molninfrastruktur 2.3.4

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Korrigerar problemet där inga poster hittades i **Rapporter** > Försäljning > **PayPal-kvittning** när du har flera PayPal-konton.

<u>Steg som ska återskapas</u>:

1. Konfigurera PayPal-kvittningsrapporter.
1. Gå till Admin, för att **Rapporter** > Försäljning > **PayPal-kvittning**.
1. Klicka på för de senaste uppdateringarna **Hämta uppdateringar** längst upp till höger.

<u>Förväntade resultat</u>:

Rapporterna ska visas.

<u>Faktiska resultat</u>:

Inget visas i rutnätet trots att rapporter är tillgängliga.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
