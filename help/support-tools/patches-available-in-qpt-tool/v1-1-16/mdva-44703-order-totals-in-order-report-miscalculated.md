---
title: 'MDVA-44703: Ordersummor i orderrapport är felberäknade'
description: MDVA-44703-korrigeringen åtgärdar ett problem där ordersummorna i Orders-rapporten är felberäknade för den begränsade administratörsanvändaren. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 är installerat. Patch-ID:t är MDVA-44703. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
exl-id: d8c31e47-ace6-4dba-a57c-941e722a6aad
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# MDVA-44703: Ordersummor i orderrapporten är felberäknade

MDVA-44703-korrigeringen åtgärdar ett problem där ordersummorna i Orders-rapporten är felberäknade för den begränsade administratörsanvändaren. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 är installerat. Patch-ID:t är MDVA-44703. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ordersummor i Orders-rapporten är felberäknade för den begränsade administratörsanvändaren.

<u>Steg som ska återskapas</u>:

1. Skapa ytterligare en webbplats med två butiker.
1. Skapa en begränsad administratörsanvändare med tillgång endast till den nya webbplatsen.
1. Logga in som begränsad administratörsanvändare.
1. Skapa två order med olika summor, en för varje ny butik.
1. Skapa fakturor för order.
1. Gå till **Rapporter** > **Försäljning** och öppna **Orderrapport**.
1. Uppdatera statistik.
1. Se rapporten för respektive butik.

<u>Förväntade resultat</u>:

Försäljningssummor motsvarar orderbeloppet för varje butik.

<u>Faktiska resultat</u>:

Den sammanlagda försäljningssumman för hela webbplatsen visas för varje butik.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
