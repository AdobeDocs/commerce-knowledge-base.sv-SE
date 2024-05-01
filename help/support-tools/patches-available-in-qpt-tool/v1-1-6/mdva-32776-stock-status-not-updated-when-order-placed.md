---
title: 'MDVA-32776: Stock-status har inte uppdaterats med orderplacering'
description: MDVA-32776-korrigeringen åtgärdar ett problem där lagerstatusen inte uppdateras när en order läggs men inte skickas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6 är installerat. Patch-ID:t är MDVA-32776. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: 10e9458f-562a-480b-b813-104a93db4308
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32776: Stock-status har inte uppdaterats med orderplacering

MDVA-32776-korrigeringen åtgärdar ett problem där lagerstatusen inte uppdateras när en order läggs men inte skickas. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6 är installerat. Patch-ID:t är MDVA-32776. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce (alla distributionsmetoder) 2.4.0

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Lagerstatusen uppdateras inte när en order placeras men inte skickas.

<u>Förutsättningar</u>:

1. Lagermodulen är installerad.
1. Visa färdiga produkter är inställt på *Ja*.

   Gå till **Lager** > **Konfiguration** > **Katalog** > **Lager** > **Visa färdiga produkter** = *Ja*.

<u>Steg som ska återskapas</u>:

1. Skapa två enkla produkter med kvantitet = 11 och 22.
1. Skapa en grupperad produkt med hjälp av de enkla produkter som skapas i steg 1.
1. Lägg grupperade produkter i varukorgen genom att ange en produktkvantitet till 11 och göra den andra enkla produkten till lagerförd.
1. Slutför utcheckningen och lägg ordern.

<u>Förväntade resultat</u>:

Visning av grupperade produkter `out-of-stock` etiketter när tillhörande enkla produkter inte finns i lager.

<u>Faktiska resultat</u>:

1. Den enkla produkten med kvantitet = 11 har slut på lager.
1. Den grupperade produkten visar inte en *lagerutfall* meddelande för produkten med kvantitet = 1. Men om du lägger till den här produkten i kundvagnen får du en *lagerutfall* fel.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
