---
title: 'MDVA-37225: Snabbordningen fungerar inte med heltal-SKU'
description: MDVA-37225-kvalitetskorrigeringen för Adobe Commerce åtgärdar problemet när sidan inte läses in när en snabborder skapas när det finns ett heltalsvärde i importerade SKU:er. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 är installerat. Patch-ID:t är MDVA-37225. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.
exl-id: ecd2b9d7-ca68-4372-b0c5-55e2a3301586
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-37225: Snabbordningen fungerar inte med heltal-SKU

MDVA-37225-kvalitetskorrigeringen för Adobe Commerce åtgärdar problemet när sidan inte läses in när en snabborder skapas när det finns ett heltalsvärde i importerade SKU:er. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 är installerat. Patch-ID:t är MDVA-37225. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

* Korrigeringen har utformats för Adobe Commerce i molninfrastrukturen 2.4.1-p1
* Korrigeringen är även kompatibel med Adobe Commerce lokalt och Adobe Commerce i molninfrastrukturen 2.4.1-2.4.2-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Förutsättning</u>:

Adobe Commerce med en installerad B2B-modul

<u>Steg som ska återskapas</u>:

1. Aktivera B2B-funktioner för snabb beställning.
1. Skapa fyra enkla produkter med SKU:er (exempel: *00100*, *001E002*, *001E02C* och *7100824*).
1. Gå till sidan ``<storefront_url>/quickorder`` i förgrunden och försök skapa en beställning med hjälp av en CSV-fil med det här exempelinnehållet:

| sku | kvantitet |
|---|---|
| 00100 | 1 |


<u>Förväntade resultat</u>:

Produkten (Exempel: produkt med SKU = *00100*) läggs till i kundvagnen som förväntat.

<u>Faktiska resultat</u>:

Sidan läses inte in och inga produkter läggs till i kundvagnen.


## Tillämpa korrigeringen

Använd följande länkar i utvecklardokumentationen, beroende på vilken Adobe Commerce-produkt du har, för att tillämpa enskilda korrigeringsfiler:

* Lokalt om Adobe Commerce och Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html)

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar i vår kunskapsbas finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Mer information om andra korrigeringsfiler som är tillgängliga i QPT-verktyget finns i avsnittet [Patchar i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) i vår supportkunskapsbas.
