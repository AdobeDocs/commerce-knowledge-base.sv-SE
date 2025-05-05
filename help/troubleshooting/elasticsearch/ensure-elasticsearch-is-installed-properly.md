---
title: Kontrollera att Elasticsearch är korrekt installerat
description: I den här artikeln beskrivs lösningar på problem som orsakas av felaktig installation och konfiguration av Elasticsearch (ES).
exl-id: d2c5971c-4db4-4857-ae79-970313bce981
feature: Install
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Kontrollera att Elasticsearch är korrekt installerat

I den här artikeln beskrivs lösningar på problem som orsakas av felaktig installation och konfiguration av Elasticsearch (ES).

>[!WARNING]
>
>Observera att uppgraderingar av tjänster inte kan implementeras i produktionsmiljön utan att vårt infrastrukturteam får 48 arbetstimmar varsel om detta på Adobe Commerce molninfrastruktur. Detta är nödvändigt eftersom vi måste se till att det finns en infrastruktursupporttekniker tillgänglig som kan uppdatera din konfiguration inom en önskad tidsram med minimala driftavbrott i din produktionsmiljö. Så 48 timmar före när dina ändringar behöver vara i produktion skickar [en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) med information om den serviceuppgradering du behöver och när du vill att uppgraderingsprocessen ska börja.

## Versionskompatibilitet för Elasticsearch med Adobe Commerce

* Adobe Commerce lokalt och Adobe Commerce i molninfrastruktur:
   * v2.2.3+ stödjer ES 5.x
   * v2.2.8+ och v2.3.1+ har stöd för ES 6.x
   * ES v2.x och v5.x rekommenderas inte på grund av [slutet på livscykeln](https://www.elastic.co/support/eol). Om du har Adobe Commerce v2.3.1 och vill använda ES 2.x eller ES 5.x måste du [Ändra Elasticsearch PHP-klienten](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/search/overview-search).
* Magento Open Source v2.3.0+ stöder ES 5.x och 6.x (men 6.x rekommenderas).

## Problem

Följande symtom tyder på att Elasticsearch inte är korrekt konfigurerat:

* `Error: No alive nodes in your cluster` - det här felet kan visas i Adobe Commerce-loggar:
   * `var/log/system.log`
   * `var/log/support_report.log`
   * `var/log/cron.log`
   * `var/log/exception.log`
   * eller i uppmaningen (när du till exempel kör en omindexering)
* Fel som anger att Elasticsearch inte är kompatibel med din nuvarande version av Adobe Commerce (detta är ett Adobe Commerce-fel som gäller för molninfrastruktur):

  ```
  [YYYY-MM-DD HH:MM:SS] CRITICAL: Fix configuration with given suggestions:    - Elasticsearch version #<version> is not compatible with current version of magento    Upgrade elasticsearch version to ~5.0
  ```

Där *version* är Elasticsearch-tjänsten som körs i molnmiljön.

## Orsak

Elasticsearch är inte korrekt installerat. Detta kan bero på:

* Ett stavfel i konfigurationsfilen.
* En version i konfigurationsfilen som inte matchar någon version av Elasticsearch som är installerad för miljön.
* En version som är korrekt installerad i miljön, korrekt konfigurerad i konfigurationsfilen, men som inte stöds för den installerade versionen av Adobe Commerce.

## Lösning

Så här konfigurerar du Elasticsearch:

* Handlare på Adobe Commerce i molninfrastruktur kan följa stegen i vår utvecklardokumentation: [Konfigurera tjänsten Elasticsearch](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch).
* Handlare på Adobe Commerce lokalt och Magento Open Source kan följa stegen i vår utvecklardokumentation: [Installera och konfigurera Elasticsearch](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/search/overview-search).

När du har konfigurerat Elasticsearch kontrollerar du att det är korrekt konfigurerat:

1. Logga in på servern.
1. Kontrollera versionsnumret för Elasticsearch (2.x, 5.x eller 6.x) i utdata om att kommandot körs: `curl -XGET <Elasticsearch hostname>:<Elasticsearch server port>` I Adobe Commerce om molninfrastruktur: `curl -XGET localhost:9200`
1. Kontrollera vad som har konfigurerats i Adobe Commerce för konfiguration av molninfrastruktur genom att köra kommandot: `php bin/magento config:show catalog/search`
1. Kontrollera `catalog/search/engine` och se till att den matchar versionsnumret för Elasticsearch. I Adobe Commerce om molninfrastruktur:
   * Elasticsearch 5.X - elasticsearch5
   * Elasticsearch 6.X - elasticsearch6
   * Elasticsearch 2.X - elasticsearch
1. Kontrollera `index_prefix`. Om du har flera miljöer måste du se till att du har olika `index_prefix`-värden för dem.
