---
title: Distributionsfel från aktivering av tidig alfavärde-modulen
description: Handlaren får installationsfel när Baler-modulen används i en produktionsmiljö, eftersom funktionen för närvarande är i ett tidigt utvecklingsstadium.
exl-id: 6cdac0a5-eaeb-467d-8369-9017aed6219e
feature: Build, Deploy, Extensions, SCD, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# Distributionsfel från aktivering av tidig alfavärde-modulen

Handlaren får installationsfel när Baler-modulen används i en produktionsmiljö, eftersom funktionen för närvarande är i ett tidigt utvecklingsstadium.

>[!WARNING]
>
>Javascript-paketering med tidig alfabalering är inte redo för användning i produktionen och används på egen risk.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.3.x och 2.4.x.
* Adobe Commerce lokal 2.3.x och 2.4.x.

## Problem

Vi rekommenderar inte att handlare använder Baler-modulen i en produktionsmiljö, eftersom den för närvarande är i ett tidigt utvecklingsskede. Om du använder den kan det leda till distributionsfel.

<u>Steg som ska återskapas</u>:

1. Handlaren försöker infoga variabeln **SCD\_USE\_BALER** i byggfasen av filen `.magento.env.yaml` som aktiverar Baler Javascript-paketeringen.
1. Handlaren lägger även till beroendet för Baler Composer: `"magento/module-baler": "1.0.0-alpha"` i `require`-avsnittet i `composer.json`.

<u>Förväntat resultat</u>:

Distributionen lyckades.

<u>Faktiskt resultat</u>:

Handlaren ser följande felmeddelande i distributionsloggarna i molnet, som är `<project home>/var/log/cloud.log`, på den statiska innehållsdistributionsfasen:

```
[2020-08-19 12:06:12] WARNING: [1007] Baler JS bundling cannot be used because of the following issues:
        [2020-08-19 12:06:12] WARNING:  - Path to baler executable could not be found. The Node package may not be installed or may not be linked.
```

## Orsak

Modulen Baler är för närvarande i det tidiga alfaversionssteget och installationen av Baler-tillägget är komplex.

## Lösning

Du kan läsa dokumentationen för Baler Alpha på [Github/Magento/Baler/Getting started with the alpha](https://github.com/magento/baler/blob/master/docs/ALPHA.md). Den är dock inte redo för produktion och används på egen risk. Vi rekommenderar istället att du sammanfogar eller paketerar JavaScript-filer (JS) med Adobe Commerce inbyggda paketering (grundläggande paketering) för filoptimering.

* Du kan aktivera sammanslagning eller paketering i administratören (sammanslagning och paketering kan inte aktiveras samtidigt): **Lagrar** > **Inställningar** > **Konfiguration** > **Avancerat** > **Utvecklare** > **JavaScript-inställningar**.
* Du kan även aktivera Adobe Commerce inbyggda paketering (grundläggande paketering) från kommandoraden: `php -f bin/magento config:set dev/js/enable_js_bundling 1`

Mer information finns i [Optimering av CSS- och Javascript-filer på Adobe Commerce i molninfrastrukturen och Adobe Commerce lokalt](https://support.magento.com/hc/en-us/articles/360044482152).
