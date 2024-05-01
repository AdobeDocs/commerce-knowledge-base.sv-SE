---
title: 'MDVA-32313-korrigering: produkter som lagts till i önskelistan med fel konfiguration'
description: MDVA-32313-korrigeringen löser problemet där konfigurerbara produkter inte kan läggas till korrekt i önskelistan, eftersom de tilldelas fel konfigurationer när de läggs till i önskelistan. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10 är installerat. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.2.
exl-id: e7ac5ef5-1389-4108-b2bc-73d43eb3e7ca
feature: Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# MDVA-32313-korrigering: produkter som lagts till i önskelistan med fel konfiguration

MDVA-32313-korrigeringen löser problemet där konfigurerbara produkter inte kan läggas till korrekt i önskelistan, eftersom de tilldelas fel konfigurationer när de läggs till i önskelistan. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10 är installerat. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.2.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce om molninfrastruktur 2.3.0

**Kompatibel med Adobe Commerce:**

Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.0 - 2.3.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Skapa en kund.
1. Logga in på kundkontot.
1. Navigera till **Produktlista** sida.
1. Välj en konfigurerbar produkt (exempel: *konfigurerbar\_1* ) och väljer önskade färg- och storleksalternativ på **Produktlista** sida (**Öppna inte produktsidan.**).
1. Klicka på önskelikonen för en annan konfigurerbar produkt (Exempel: *konfigurerbar\_2*) på samma sida utan att välja några färg- eller storleksalternativ.

<u>Förväntade resultat</u>:

The *konfigurerbar\_2* produkten läggs till i önskelistan utan valda alternativ, som förväntat.

<u>Faktiska resultat</u>:

The *konfigurerbar\_2* produkten har lagts till i önskelistan med konfigurationen från *konfigurerbar\_1* produkt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
