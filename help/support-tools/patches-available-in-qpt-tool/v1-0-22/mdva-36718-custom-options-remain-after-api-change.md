---
title: 'MDVA-36718: Anpassade alternativ kvarstår efter API-ändring'
description: MDVA-36718 Magento-korrigeringen åtgärdar problemet när de gamla anpassade alternativen kvarstår efter att de har ändrats via API.
exl-id: e9755764-e563-4921-af75-a90e06237053
feature: REST
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# MDVA-36718: Anpassade alternativ behålls efter API-ändring

MDVA-36718 Magento-korrigeringen åtgärdar problemet när de gamla anpassade alternativen kvarstår efter att de har ändrats via API.

Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 är installerat. Patch-ID:t är MDVA-36718. Observera att problemet är planerat att åtgärdas i Magento version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce i molninfrastruktur 2.4.1

**Kompatibel med Magento-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.3.0-2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt.
1. Lägg till en **nedrullningsbar typ** anpassat alternativ.
1. Uppdatera det anpassade alternativet via API: Skicka `PUT` begäran till `/V1/products/options/{optionId}`.

<u>Förväntade resultat</u>:

De anpassade alternativen uppdateras som förväntat.

<u>Faktiska resultat</u>:

Nya anpassade alternativ läggs till, men de gamla anpassade alternativen finns kvar.

## Tillämpa korrigeringen

Om du vill tillämpa enskilda korrigeringsfiler använder du följande länkar beroende på distributionsmetod:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera korrigering för problem med Magento med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som finns i QPT-verktyget finns i [Patchar tillgängliga i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
