---
title: "MDVA-15546: Kolumnen 'entity_id' där -satsen är tvetydig"
description: "MDVA-15546-korrigeringen åtgärdar prestandaproblem som kan uppstå i samband med vissa Amazon-tillägg. Detta fel visas i följande felmeddelanden i undantagsloggar: *där*   *Kolumnen 'entity\\_id' där satsen är tvetydig, frågan var: SELECT \\`main\\_table\\'.\\*, \\`extension\\_attribute\\_amazon\\_order\\_reference\\_id* \\`. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 är installerat. Patch-ID:t är MDVA-15546."
exl-id: d58c1728-eb7a-49e8-a329-3197f2339b9c
feature: B2B, Commerce Intelligence
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-15546: Kolumnen &#39;entity_id&#39; där -satsen är tvetydig

MDVA-15546-korrigeringen åtgärdar prestandaproblem som kan vara relaterade till vissa Amazon-tillägg. Det här problemet indikeras av följande fel i undantagsloggar: *where*   *Kolumnen &#39;entity\_id&#39; där satsen är tvetydig, frågan var: SELECT \`main\_table\&#39;.\*, \`extension\_attribute\_amazon\_order\_reference\_id* \`. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 är installerat. Patch-ID:t är MDVA-15546.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce om molninfrastruktur 2.2.5

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce om molninfrastruktur 2.3.0 - 2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Prestandaproblem som kan vara relaterade till vissa Amazon-tillägg.

<u>Förutsättningar</u>:

Rensa Adobe Commerce med B2B och Amazon\_Payment.

<u>Steg som ska återskapas</u>:

1. Gå till butikssidan.
1. Lägg produkten i kundvagnen.
1. Vänta eller utlösa cron-jobbet `flush_preview_quotas`.

<u>Faktiskt resultat</u>:

När du kontrollerar `var/log/exception/log` visas följande fel:

*`report.ERROR: Cron Jobflush_preview_quotashas an error: SQLSTATE[23000]: Integrity constraint violation: 1052 Column 'entity_id' in where clause is ambiguous, query was: SELECT `main_table`.*, `extension_attribute_amazon_order_reference_id`.`amazon_order_reference_id` AS `extension_attribute_amazon_order_reference_id_amazon_order_reference_id`, `extension_attribute_amazon_order_reference_id`.`quote_id` AS `extension_attribute_amazon_order_reference_id_quote_id`, `_attribute_amazon_order_reference_id`.` sandbox_simulation_reference` AS `extension_attribute_amazon_order_reference_id_sandbox_simulation_reference`, `extension_attribute_amazon_order_reference_id`.`confirm` AS `extension_attribute_amazon_order_reference_id_confirmation` AS `main_table ` LEFT JOIN `amazon_quote` AS `extension_attribute_amazon_order_reference_id` ON main_table.entity_id = extension_attribute_amazon_order_reference_id.quote_id WHERE ...`*` FROM `

<u>Förväntat resultat</u>:

Cron Job slutförs utan fel.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
