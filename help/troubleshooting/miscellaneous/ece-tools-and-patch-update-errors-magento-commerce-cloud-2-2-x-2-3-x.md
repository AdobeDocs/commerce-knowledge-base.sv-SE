---
title: ECE-verktyg och korrigeringsuppdateringsfel Adobe Commerce cloud infrastructure 2.2.x, 2.3.x
description: Den här artikeln innehåller en lösning på problemet där felmeddelanden visas, t.ex. "*failed to open stream:*" eller "*No such file or directory*" vid försök att distribuera uppdateringar till ECE-verktyg, korrigeringar eller andra ändringar.
exl-id: b1658001-0ffd-4f8a-a15f-d785efcee51f
feature: Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# ECE-verktyg och korrigeringsuppdateringsfel Adobe Commerce cloud infrastructure 2.2.x, 2.3.x

Den här artikeln innehåller en lösning på problemet där felmeddelanden visas, t.ex. *inte kunde öppna dataström:* eller *ingen sådan fil eller katalog* när du försökte distribuera uppdateringar till ECE-verktyg, korrigeringsfiler eller andra ändringar.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur 2.2.x, 2.3.x

## Problem

Fel uppstod vid försök att distribuera uppdateringar till ECE-verktyg, korrigeringar eller andra ändringar: PHP-fel i molnkonsolen och i `var/log/cloud.log`

```
W: PHP Warning: require(<path to file>): failed to open stream: No such file or directory in <path to file> on line 70
W: PHP Fatal error: require(): Failed opening required '<path to file>;'
(include_path='<path to file>') in <path to file> on line 70

Warning: require(/app/vendor/composer/../../app/etc/NonComposerComponentRegistration.php):
failed to open stream: No such file or directory in /app/vendor/composer/autoload_real.php
on line 70

Fatal error: require(): Failed opening required '/app/vendor/composer/../../app/etc/NonComposerComponentRegistration.php'
(include_path='/app/vendor/magento/zendframework1/library:.:/usr/share/php')
in /app/vendor/composer/autoload_real.php on line 70

E: Error building project: Step failed with status code 255.
```

Fel i undantagsloggen:

```
CRITICAL:
error: <path to missing file>: No such file or directory
```

```
W: Generating optimized autoload files
W: PHP Warning: Uncaught ErrorException: require(<path to file>):
failed to open stream: No such file or directory in <path to file>
```

```
PHP Warning: Uncaught Exception: Warning: require(/app/setup/config/application.config.php):
failed to open stream: No such file or directory in /app/vendor/magento/framework/Console/Cli.php
on line 63 in /app/vendor/magento/framework/App/ErrorHandler.php:61
```

```
[Symfony\Component\Console\Exception\CommandNotFoundException]
 W: There are no commands defined in the "module" namespace.
```

## Orsak

Felkonfiguration av din `composer.json`-fil.

## Lösning

Om en inställning saknas i din `composer.json`-fil kopieras inte vissa kataloger från Adobe Commerce Code Base. Paketet och uppdateringen/korrigeringen kan inte tillämpas eftersom filer inte hittas.

Ändra det extra avsnittet så att det matchar det som anges nedan och försök sedan distribuera igen.

```
"extra":{
  "magento-force": true,
  "magento-deploystrategy": "copy"
}
```

## Relaterad läsning

* [Uppgraderingar och korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/best-practices) i utvecklardokumentationen.
