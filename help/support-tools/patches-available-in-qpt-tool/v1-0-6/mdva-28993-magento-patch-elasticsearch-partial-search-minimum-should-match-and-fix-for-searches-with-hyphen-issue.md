---
title: 'MDVA-28993: partiell sökning i Elasticsearch, "minimum should match" och fix for "searches with binphen" issue'
description: MDVA-28993-korrigeringen implementerar funktionen"Minimum should match" och partiell sökning för Elasticsearch-motorn, och löser problem med bindestreck i sökfrågor. Korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 är installerat.
exl-id: 2af0f950-284b-42f2-9660-8aafce4b04d7
feature: Search, Services
role: Admin
source-git-commit: 6f4d6382cbdb7bedddcc3f264fbf6ef997729323
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-28993: partiell sökning i Elasticsearch, &quot;minimum should match&quot; och korrigering för &quot;searches with binphen&quot; issue

MDVA-28993-korrigeringen implementerar funktionen&quot;Minimum should match&quot; och partiell sökning för Elasticsearch-motorn, och löser problem med bindestreck i sökfrågor. Korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 är installerat.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-version:** Adobe Commerce i molninfrastruktur 2.3.4

**Kompatibel med Adobe Commerce-versioner:** Adobe Commerce lokalt/Adobe Commerce i molninfrastruktur 2.3.4-2.3.5-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.


## Problem

När du använder Elasticsearch 6 för att söka efter SKU som innehåller ett bindestreck (-) returneras för många resultat.

<u>Steg att återskapa:</u>

1. Gå till butiken.

1. I sökfältet anger du en sträng som innehåller ett bindestreck, till exempel &quot;WS-M-Blue&quot;.

<u>Förväntat resultat:</u>

Returnerar endast WS-M-Blue.

<u>Faktiskt resultat:</u>

Returnerar alla SKU:er som börjar med WS.

## Lappningsinformation

MDVA-28993-korrigeringen innehåller följande korrigeringar och förbättringar:

* implementerar den nya funktionen&quot;Minimum should match&quot; och partiell sökning för Elasticsearch-motorn. Mer konfigurationsinformation finns i [Konfigurera katalogsökning](https://docs.magento.com/user-guide/catalog/search-configuration.html#step-4-configure-minimum-terms-to-match) i användarhandboken.
* partiell sökning i Elasticsearch
* åtgärdar problemet&quot;sökningar med bindestreck&quot; som beskrivs ovan.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
