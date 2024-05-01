---
title: "MDVA-37182: inkonsekventa sökresultat i Elasticsearch 6 och 7"
description: Korrigeringen MDVA-37182 åtgärdar ett problem med inkonsekvent sökbeteende i olika versioner 6 och 7 av Elasticsearch. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 är installerat. Patch-ID:t är MDVA-37182. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.
exl-id: 6c4e2d2f-cced-487d-b253-fd0c80bc6067
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-37182: inkonsekventa sökresultat i Elasticsearch 6 och 7

Korrigeringen MDVA-37182 åtgärdar ett problem med inkonsekvent sökbeteende i olika versioner 6 och 7 av Elasticsearch. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 är installerat. Patch-ID:t är MDVA-37182. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:** Adobe Commerce i molninfrastruktur 2.4.1

**Kompatibel med Adobe Commerce:** Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.4.1-2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Inkonsekvent sökbeteende.

<u>Steg som ska återskapas</u>:

1. Skapa produkter med följande information:
   * Namn: &quot;5127AC&quot;, &quot;5127SS&quot;, &quot;5127AB&quot;
   * SKU: &quot;product1&quot;, &quot;product2&quot;, &quot;product3&quot;
1. Ställ in sökmotorn på Elasticsearch 6 (ES6).
1. Kör fullständig omindexering.
1. Sök efter &quot;5127s&quot; i butiken.
1. Ställ in sökmotorn på Elasticsearch 7 (ES7).
1. Kör fullständig omindexering.
1. Sök efter &quot;5127s&quot; i butiken.

<u>Faktiskt resultat:</u>:

ES6: sökningen returnerar inga resultat.ES7: sökningen returnerar tre produkter.

<u>Förväntat resultat:</u>:

Sökningen returnerar en produkt för båda versionerna.

## Tillämpa korrigeringen

Använd följande länkar, beroende på vilken Adobe Commerce-produkt du använder, för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som finns i QPT-verktyget finns i [Patchar tillgängliga i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
