---
title: Driftsättningen misslyckas med snabb inkompatibel Adobe Commerce-version
description: 'UPPDATERAD: 29 februari 2019'
exl-id: aab77407-94e5-42de-92f4-2f0c19e24fa4
feature: Deploy, Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Driftsättningen misslyckas med snabb inkompatibel Adobe Commerce-version

UPPDATERAD: 29 februari 2019

Den här artikeln innehåller en korrigering för när distributionen misslyckas eftersom modulen Snabbt inte är kompatibel med din nuvarande Adobe Commerce-version.

**Problem:** Distributionen misslyckas efter en ny implementering och push, med felmeddelandet som liknar följande:

>\[Exception\] Varning: Argument 3 saknas för Fastly\\Cdn\\Plugin\\..., anropas i /app/vendor/magento/framework/Interception/Interceptor.php ... och definieras i /app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php ...

**Orsak:** inkompatibla ändringar i snabbmodulen v1.2.79 har gjorts bakåt.

**Lösning (tillfällig):** Uppgradera snabbmodulen till version 1.2.82 eller senare och överför en ny VCL i Commerce Admin. Sedan implementera och push-styr du ändringarna för att få en lyckad distribution.

## Berörda versioner

* Adobe Commerce lokal 2.1.X
* Adobe Commerce i molninfrastruktur 2.1.X
* Snabb modul 1.2.79

## Problem

När du implementerar och överför dina ändringar till integrerings-, produktions- eller mellanlagringsmiljön är vanligtvis nästa steg att utlösa distributionsprocessen. Detta görs automatiskt i Adobe Commerce i molninfrastrukturutgåvan och manuellt i Adobe Commerce lokalt.

Distributionen kan misslyckas med följande felmeddelanden:

```
[2019-01-23 00:00:00] INFO: php ./bin/magento setup:static-content:deploy --ansi --no-interaction --jobs 1 --exclude-theme Magento/luma en_GB en_US
[2019-01-23 00:00:00] CRITICAL:
  Requested languages: en_GB, en_US
  Requested areas: frontend, adminhtml
  Requested themes: Magento/blank, Magento/backend
  === frontend -> Magento/blank -> en_GB ===

    [Exception]
    Warning: Missing argument 3 for Fastly\Cdn\Plugin\ExcludeFilesFromMinification::afterGetExcludes(), called in /app/vendor/magento/framework/Interception/Interceptor.php on line 152 and defined in /app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php on line 38

  setup:static-content:deploy [-d|--dry-run] [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [-t|--theme[="..."]] [--exclude-theme[="..."]] [-l|--language[="..."]] [--exclude-language[="..."]] [-a|--area[="..."]] [--exclude-area[="..."]] [-j|--jobs[="..."]] [--symlink-locale] [languages1] ... [languagesN]

[2019-01-23 000:00:00] INFO: Set flag: var/.deploy_is_failed
[2019-01-23 00:00:00] CRITICAL: Command php ./bin/magento setup:static-content:deploy --ansi --no-interaction --jobs 1 --exclude-theme Magento/luma en_GB en_US returned code 1
```

Om du använder Adobe Commerce i molninfrastrukturslösningen visas det här felmeddelandet i [distributionsloggen](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/test/log-locations). För Adobe Commerce lokalt visas felet på kommandoraden.

## Orsak

Problemet orsakas av bakåtkompatibla ändringar i snabbmodulen v1.2.79.

## Lösning

Uppgradera modulen Snabbt till version 1.2.82 eller senare.

Gör så här:

1. Kör något av följande kommandon:
   * om Fastly-modulen ingår i magento-cloud-metapackage:    <pre>Composer update magento/magento-cloud-metapackage</pre>
   * om modulen Fastly installerades separat (om du till exempel använder Adobe Commerce lokalt, inte molnutgåvan) <pre>snabbuppdatering/magento2</pre>
1. Genomför och skicka ändringarna och utlösa distributionsprocessen om det inte görs automatiskt.
1. I Admin [överför du den nya VCL:en till Snabbt](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#upload-vcl-snippets).
