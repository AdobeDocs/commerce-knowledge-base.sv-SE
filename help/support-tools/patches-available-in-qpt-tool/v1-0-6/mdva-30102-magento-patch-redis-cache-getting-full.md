---
title: 'MDVA-30102: Redis-cachen börjar bli full'
description: MDVA-30102-korrigeringen löser problemet med att Redis-cachen är full och genererar fel, vilket orsakar problem med produktlistningssidor (PLP) och produktinformationssidor (PDP), t.ex. saknade produkter. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.6 är installerat.
exl-id: 34772296-8c93-471c-b5ad-6815adb78ca6
feature: Cache, Categories, Services
role: Admin
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# MDVA-30102: Redis-cachen börjar bli full

MDVA-30102-korrigeringen löser problemet med att Redis-cachen är full och genererar fel, vilket orsakar problem med produktlistningssidor (PLP) och produktinformationssidor (PDP), t.ex. saknade produkter. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.6 är installerat.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce om molninfrastruktur 2.3.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.2 - 2.4.1-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Redis-cachen börjar bli full och den allokerade `maxmemory` verkar vara otillräcklig. Layoutcachen hade inte TTL-värde och har inte avlägsnats, vilket medförde att andra nycklar i Redis ökade och avlägsnades. Därför allokerades allt Redis-minne för layoutcache.

<u>Förutsättningar</u>:

* Användaren måste befinna sig i Adobe Commerce 2.4 och ha 100 000 enkla produkter (produkttypen har ingen betydelse) samt 50 kategorier.
* Redis-cachen måste konfigureras enligt stegen i [Adobe Commerce Configuration Guide > Use Redis for the Adobe Commerce page and default cache](https://devdocs.magento.com/guides/v2.4/config-guide/redis/redis-pg-cache.html#example-command) i vår dokumentation för utvecklare.

<u>Steg som ska återskapas</u>:

1. Bläddra bland alla PDP:er och PLP:er. Du kan använda [OWASP ZAP](https://www.zaproxy.org/) för att crawla webbplatsen.
1. Observera Redis minnesanvändning.
1. Kontrollera även aktuell konfiguration och använt minne. Kör följande kommando i CLI. Den söker efter använt minne, maximalt minne, borttagna nycklar och Redis-upptid i dagar:

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

<u>Förväntade resultat</u>:

Redis-cachen bör inte växa snabbt.

<u>Faktiska resultat</u>:

Redis-cachen växer upp till ~5 GB. Det finns en maxgräns på 8 GB Redis-minne, så om du har 1 MB-produkter kommer du snabbt att få slut på minne.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
