---
title: Spårningsindex för ElasticSuite orsakar problem med Elasticsearch
description: I den här artikeln behandlas problemet med minnesproblem i Elasticsearch som orsakas av att man håller reda på index som skapats med pluginprogrammet ElasticSuite.
exl-id: 67bfd06a-c801-4306-8510-a84a6fe5351a
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# Spårningsindex för ElasticSuite orsakar problem med Elasticsearch

>[!NOTE]
>
>ElasticSuite och dess tillhörande program är tredjepartsverktyg som för närvarande inte stöds av Adobe. Det här innehållet presenteras endast som information och inte som en indikation på vad som är aktiverat för supportavtal.

I den här artikeln behandlas problemet med minnesproblem i Elasticsearch som orsakas av att man håller reda på index som skapats med pluginprogrammet ElasticSuite.

## Berörda produkter och versioner

ElasticSuite-versioner före 2.8.0 kan inte regelbundet rensa upp spårningsindex.

ElasticSuite-versioner före 2.9.8 / 2.10.7 lagrar spårningsindex i dagliga index, vilket gör att antalet öppna index ökar.

## Problem

Om ElasticSuite-pluginprogrammet från en annan leverantör är installerat kan du få minnesproblem i Elasticsearch och tjänsten Elasticsearch kan krascha på grund av ElasticSuite-spårningsindex. Symtomen är bland annat:

* Elasticsearch kraschar utan minnesfel.
* När du kör ett hälsokommando `curl -m1 localhost:9200/_cluster/health?pretty` eller `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty` (för startkonton) finns det hundratals eller tusentals `unassigned_shards`
* Elasticsearch eller webbplatsens prestanda försämras avsevärt.
* *&quot;Inga aktiva noder hittades i ditt kluster&quot;* i Elasticsearch, driftsättnings- eller loggfel.
* *&quot;Avvisar mappningsuppdatering till [&lt;\*>_ tracking_log_event _&lt;\*>]&quot;* vid distribution eller loggfel.

## Orsak

ElasticSuite har en ny funktion som skapar spårningsindex. Dessa spårningsindex registrerar vilka söktermer som används mest, vilket innebär att omsättningen blir störst och vilka termer som leder till att ingen resultatsida visas så att säljarna kan skapa synonymer för att åtgärda dem. Spårningsindexen verkar inte tas bort, så Elasticsearch har slut på resurser och krascher.

## Lösning

### Uppgradera din version av Elastic Suite så att du kan rensa spårningsindex med jämna mellanrum

När du har uppgraderat ElasticSuite-pluginen till version högre än 2.8.0 kan du konfigurera en regelbunden rensning av index.

Gå till **Lager** > **Konfiguration** > **Spårning** > **Global konfiguration** > **Kvarhållningsfördröjning**

Standardkvarhållningsperioden är 365 dagar. Du kan minska den till 30 eller 15 dagar.

### Uppgradera din version av Elastic Suite så att du kan använda månatliga index istället för dagliga index

När du har uppgraderat ElasticSuite-pluginen till version > 2.9.8/2.10.7, kommer spärrindex att baseras på månadsvis uppföljning.

Du kan fortfarande minska kvarhållningsperioden:

Gå till **Lager** > **Konfiguration** > **Spårning** > **Global konfiguration** > **Kvarhållningsfördröjning**

Standardkvarhållningsperioden är 12 månader (genererar 12 index). Du kan minska den till 3 eller 6 månader.

### Använd ett cronjob för att rensa spårningsindexdata

Skapa ett cron-jobb för att ta bort spårningsindex. Med det här kommandot tas index som skapats den senaste månaden bort:

```
   curl -XDELETE localhost:9200/<name in index> * **\_tracking\_log** * _$(date
    +'%Y%m' -d 'last month')*
```

Om du vill ta bort index med en viss tidsfrekvens skapar du ett cron-jobb genom att läsa följande artiklar i vår utvecklardokumentation:

* [Konfigurera ett anpassat cron-jobb och en cron-grupp (självstudiekurs)](https://devdocs.magento.com/guides/v2.3/config-guide/cron/custom-cron-tut.html)
* [Ställ in cron-jobb](https://devdocs.magento.com/guides/v2.3/cloud/configure/setup-cron-jobs.html)
