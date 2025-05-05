---
title: Elasticsearch-indexstatus är "gul" eller "röd"
description: Artikeln innehåller en korrigering för när indexstatusen för Elasticsearch inte är '*green*'. '*yellow*' anger normal och '*red*' anger felaktig. "Gul" eller "röd" kan förekomma i samband med att produkter saknas eller att gammal produktinformation visas.
exl-id: 27689511-6a41-41a9-8dda-a627d2f65263
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Elasticsearch-indexstatus är &quot;gul&quot; eller &quot;röd&quot;

>[!WARNING]
>
> [MySQL-katalogsökmotorn tas bort i Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Du måste ha konfigurerat värddatorn Elasticsearch innan du kan installera version 2.4.0. Se [Installera och konfigurera Elasticsearch](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/search/overview-search).

Artikeln innehåller en korrigering när indexstatusen för Elasticsearch inte är *grön*. *gul* anger normal och *röd* anger felaktig. &quot;Gul&quot; eller &quot;röd&quot; kan förekomma i samband med att produkter saknas eller att gammal produktinformation visas.

## Berörda versioner och produkter

* Adobe Commerce om molninfrastruktur 2.2.x, 2.3.x
* Adobe Commerce lokalt 2.2.x, 2.3.x

## Problem

Sökindexet för Elasticsearch-katalogen är långsamt, vilket resulterar i statusen *yellow* eller *red* i stället för *green*. Du kan även upptäcka att ändringar saknas i förgrunden.

## Orsak

Det kan finnas flera möjliga orsaker. En orsak är att diskutrymmet håller på att ta slut i Elasticsearch-instansen. En annan orsak är dubblerade index.

## Lösning

Skapa en ny mysql-dump innan du följer de här stegen och utför dem utanför kontorstid för att undvika att dina kunder påverkas:

1. Växla tillfälligt till MySQL-sökning - aktivera MySQL-sökning. (Obs! Kom ihåg att växla tillbaka till Elasticsearch, annars kan du få prestandaproblem.)
1. Identifiera duplicerade index genom att köra följande kommando:

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

1. Så här tar du bort index:

   ```
   curl -XDELETE localhost:9200/[your_index_name_here]
   ```

1. Återaktivera Elasticsearch.
1. Kör fullständig omindexering.
1. Kontrollera indexstatus genom att köra följande kommando:

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

Om de här stegen inte fungerar skickar [en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Relaterad läsning

Mer information finns i [Elasticsearch Cluster Health API](https://www.elastic.co/guide/en/elasticsearch/reference/current/cluster-health.html).
