---
title: Aktivera cache för att undvika prestandaförsämring
description: I den här artikeln beskrivs hur du löser ett långsamt webbplatsproblem som orsakas av att vissa Adobe Commerce-cachetyper har inaktiverats.
exl-id: e4e5a753-efa3-4552-aaf6-28e44efcfa5b
feature: Cache, Observability
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Aktivera cache för att undvika prestandaförsämring

I den här artikeln beskrivs hur du löser ett långsamt webbplatsproblem som orsakas av att vissa Adobe Commerce-cachetyper har inaktiverats.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.2.x, 2.3.x
* Adobe Commerce lokal 2.2.x, 2.3.x

## Problem

Prestandan försämras. Exempelvis läses utcheckningssidan in långsamt eller så minskar Apdex-värdet i New Relic.

## Orsak

En orsak till prestandaförsämring kan vara att vissa cachetyper i Adobe Commerce inaktiveras.

## Lösning

1. Kontrollera först statusen för din Adobe Commerce-cache för att se om detta är problemet. För detta [SSH till din miljö](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) och kör följande kommando:

   ```bash
   php bin/magento cache:status
   ```

   Då visas status för varje cachetyp (&quot;0&quot; för inaktiverad, &quot;1&quot; för aktiverad). Du kan också hämta den här informationen i filen `app/etc/env.php`.

1. Undersök de inaktiverade cachetyperna. Alla cachetyper för Adobe Commerce ska vara aktiverade, såvida du inte fått någon alternativ vägledning från Adobe. Tillägg från tredje part får inte kräva att Adobe Commerce-cache inaktiveras.
1. Om undersökningen bekräftar att vissa cachetyper har inaktiverats av misstag kan du aktivera dem genom att köra följande kommando för varje cachetyp: `php bin/magento cache:enable <your_disabled_cache_type>`

[Kontakta Adobe Commerce support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) och be om råd om du har frågor om och/eller frågor om en viss cachetyp för Adobe Commerce kan eller bör inaktiveras.

## Relaterad läsning

Dokumentation om Adobe Commerce-cache finns i vår utvecklardokumentation:

* [Översikt över Adobe Commerce-cache](https://developer.adobe.com/commerce/frontend-core/guide/caching/)
* [Hantera cachen](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-cache)

Andra möjliga orsaker till prestandaproblem och lösningar:

* [Inaktivera utdata från Adobe Commerce Banner för att förbättra webbplatsens prestanda](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md)
* [MySQL-tabeller är för stora](/help/troubleshooting/database/mysql-tables-are-too-large.md)
* [Långsamma prestanda, långsamma och långvariga kroner](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md)
* [Begränsad administratörsåtkomst som orsakar prestandaproblem](/help/troubleshooting/miscellaneous/restricted-admin-access-causing-performance-issues.md)
