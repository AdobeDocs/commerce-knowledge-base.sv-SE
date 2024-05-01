---
title: Redis-tjänsten kraschade
description: Artikeln rekommenderar hur du åtgärdar Redis.
exl-id: 5eb8fb70-0f41-433a-8d3f-c368781a2d1d
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# Redis-tjänsten kraschade

Artikeln rekommenderar hur du åtgärdar Redis.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.2.x, 2.3.x
* Adobe Commerce lokal 2.2.x, 2.3x
* Alla versioner av Redis

## Problem

Saktsamhet eller driftstopp på webbplatsen på grund av minnesspill i Redis.

## Orsak

Minnesspill kan göra att Redis-tjänsten kraschar. Under högbelastningstiden kan Redis-tjänsten behöva mer minne än vad som för närvarande är allokerat.

## Lösning

Kör följande kommando i CLI om du vill kontrollera aktuell konfiguration och använt minne. Den söker efter använt minne, maximalt minne, borttagna nycklar och Redis-upptid i dagar:

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

The *REDIS\_PORT* och *REDIS\_HOST* variabler kan hämtas från `app/etc/env.php`.

Om utdata från körning av ovanstående fråga visar att andelen ledigt minne är mindre än 40 %, [skicka en biljett till Adobe Commerce support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) begära en ökning av `maxmemory` i Redis Server. Om värdet för de borttagna tangenterna inte är &quot;0&quot; eller Redis-uppspelningstiden i dagar är lika med 0 (vilket anger att Redis har kraschat idag) bör du även [skicka en biljett till Adobe Commerce support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) begära en utredning och en korrigering av problemet.

## Relaterad läsning

Mer information om Redis-minne finns i [Redis Memory Optimization](https://redis.io/topics/memory-optimization).
