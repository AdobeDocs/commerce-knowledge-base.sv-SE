---
title: "MDVA-22026: Det går inte att importera produktbilder från en extern URL"
description: MDVA-22026-korrigeringen åtgärdar problemet med att det inte går att importera produktbilder från en extern URL.
exl-id: 29043c6c-daf2-4925-85bf-49eeeee3742c
feature: Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# MDVA-22026: Det går inte att importera produktbilder från extern URL

MDVA-22026-korrigeringen åtgärdar problemet med att det inte går att importera produktbilder från en extern URL.

Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 är installerat. Korrigerings-ID är MDVA-22026. Observera att problemet har åtgärdats i Adobe Commerce version 2.3.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:** Adobe Commerce om molninfrastruktur 2.3.2-p2

**Kompatibel med Adobe Commerce:** Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.2-2.3.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Gå till Admin **System** > **Importera**.
1. Ange **Enhetstyp** = *Produkter*.
1. Ange **Importbeteende** = *Lägg till/uppdatera*.
1. Ange **Antal tillåtna fel** = *10000*.
1. Markera filen som ska importeras.
1. Klicka på **Kontrollera data** (som ska validera filen).
1. Klicka på **Importera** -knappen.

<u>Förväntade resultat</u>:

Importen av produkter från CSV-filer, inklusive bilder från externa URL:er, lyckades som förväntat.

<u>Faktiska resultat</u>:

Importen av produkter från CSV-filer, inklusive bilder från externa URL:er, misslyckades och du får ett liknande fel:

```php
1. Imported resource (image) could not be downloaded from external resource due to timeout or access permissions in row(s): 4, 5, 8, 9, 16, 18, 20, 21, 22, 23, 26, 27, 28, 52, 53, 55, 58, 63, 70, 71, 77, 78, 83, 84, 91
```

## Tillämpa korrigeringen

Om du vill använda enskilda korrigeringsfiler använder du följande länkar beroende på distributionsmetod:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html).
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html).

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Leta efter Adobe Commerce-problem med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Mer information om andra korrigeringsfiler som finns i QPT-verktyget finns i [Patchar tillgängliga i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
