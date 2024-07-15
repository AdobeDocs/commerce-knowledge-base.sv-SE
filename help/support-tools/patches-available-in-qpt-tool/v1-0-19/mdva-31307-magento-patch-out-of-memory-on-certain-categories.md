---
title: "MDVA-31307: Slut på minne i vissa kategorier"
description: Korrigeringen MDVA-31307 åtgärdar ett problem där "Magento\_Csp/Model/BlockCache" förbrukar mycket minne och genererar enorma cachelagrade strängar, vilket orsakar problem för vissa sidor med många dynamiskt vitlistade skript och format. Den medföljande korrigeringen optimerar processen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Patch-ID:t är MDVA-31307. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: 15d82f5b-bd43-4a0a-b756-d109dac6d2cd
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-31307: Slut på minne i vissa kategorier

MDVA-31307-korrigeringen åtgärdar ett problem där `Magento\_Csp/Model/BlockCache` förbrukar mycket minne och genererar enorma cachelagrade strängar, vilket orsakar problem för vissa sidor med många dynamiskt vitlistade skript och format. Den medföljande korrigeringen optimerar processen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Patch-ID:t är MDVA-31307. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-version:** Adobe Commerce i molninfrastruktur 2.4.0

**Kompatibel med Adobe Commerce-versioner:** Adobe Commerce lokalt och Adobe Commerce i molninfrastrukturen 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Åtgärdar problemet där det finns *Slut på minne* i vissa kategorier på grund av problem med dynamisk CSP-vitlistning för cachelagrade block.

<u>Steg att återskapa:</u>

1. Generera korrigeringar för små profiler (`bin/magento setup:performance:generate-fixtures`).
1. Öppna alla kategorisidor på olika flikar.

<u>Faktiskt resultat:</u>

*[datum och tid] Allvarligt PHP-fel: Den tillåtna minnesstorleken på 1073741824 byte har uttömts (försök gjordes att allokera 90112 byte) i Okänd rad 0
[datum och tid] Allvarligt PHP-fel: Den tillåtna minnesstorleken på 1073741824 byte har uttömts (33554440 byte har allokerats) i /app/`<project-id>`/vendor/magento/module-csp/Model/Collector/DynamicCollector.php på rad 31*

<u>Förväntat resultat:</u>

Alla sidor har öppnats korrekt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
