---
title: '''MDVA-30284 Patch: Elasticsearch 7 - Limit of total fields [XXXXX] in index has been been been been been been'
description: MDVA-30284-korrigeringen löser problemet där du får ett felmeddelande om att gränsen för det totala antalet fält \[XXXXX\] i indexet har överskridits när du använder Elasticsearch 7. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.5 är installerat. Korrigerings-ID är MDVA-30284.
exl-id: cf840558-891a-4a7e-8900-b8434f703be0
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# MDVA-30284 Patch: Elasticsearch 7 - Limit of total fields [XXXXX] i index har överskridits

MDVA-30284-korrigeringen löser problemet där du får ett felmeddelande om att gränsen för det totala antalet fält \[XXXXX\] i indexet har överskridits när du använder Elasticsearch 7. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.5 är installerat. Korrigerings-ID är MDVA-30284.

## Berörda produkter och versioner

* Korrigeringen har utformats för Adobe Commerce i molninfrastrukturen 2.3.5-p2
* Elasticsearch 7 är kompatibelt med Adobe Commerce 2.3.5 och 2.4.x

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Fältgränsen för Elasticsearch är felaktig vilket resulterar i följande fel när indexeraren \[catalogsearch\_fulltext\] körs:

*Gräns för totalt antal fält [xxx] i index [xxxxxx] har överskridits*

Problemet inträffar när du har ett stort antal produktattribut. Problemet utlöses av hur Elasticsearch beräknar fältantalet. Ibland indexeras dessa fält som separata indexerare när det finns attribut som har tilldelats fält. Detta resulterar i att gränsen överskrids.

<u>Steg som ska återskapas:</u>

<u>Förutsättningar</u>

* Installerad module-elasticsearch 10.0.3.5.
* Elasticsearch 7 är installerat.
* Konfigurera Elasticsearch som en sökserverdel.

1. Skapa fler än 1 000 attribut för produkter.
1. Skapa produkter för varje familj.
1. Kör indexerare.

<u>Förväntat resultat:</u>

Alla produkter finns i indexet Elasticsearch.

<u>Faktiskt resultat:</u>

1. Fel i Elasticsearch:

   ```
    {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"}],"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"},"status":400}
   ```

1. Den nya produkten har inte indexerats.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
