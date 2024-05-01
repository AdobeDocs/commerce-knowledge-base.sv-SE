---
title: 'MDVA-31168-korrigering: Produktexportfilen visas inte i Admin'
description: Korrigeringen MDVA-31168 löser problemet där produktexportens CSV-fil inte visas i listan över exporterbara CSV-filer. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10 är installerat. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.2.
exl-id: 780a926b-2aea-47c2-8f95-907cc779bfa4
feature: Admin Workspace, Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# MDVA-31168-korrigering: Produktexportfilen visas inte i Admin

Korrigeringen MDVA-31168 löser problemet där produktexportens CSV-fil inte visas i listan över exporterbara CSV-filer. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10 är installerat. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.2.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:** Adobe Commerce lokal 2.3.5-p2.

**Kompatibel med Adobe Commerce:** Adobe Commerce i molninfrastrukturen och Adobe Commerce lokalt 2.3.0 - 2.4.1.

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Förutsättningar</u>:

Installera Adobe Commerce med exempeldata.

<u>Steg som ska återskapas:</u>

1. Skapa en nedladdningsbar produkt och tilldela den till **Påsar** kategori.
1. Starta en export för alla produkter.
1. Kör följande kommando från CLI:    ```php    bin/magento queue:consumers:start exportProcessor --single-thread --max-messages=10000    ```

<u>Förväntade resultat:</u>

Produktexportens CSV-fil med alla produkter visas som förväntat i fillistan i Admin.

<u>Faktiska resultat:</u>

Produktexportens CSV-fil med alla produkter visas inte i Admin-listan, men filen med endast rubriker genereras i `/var` på servern.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
