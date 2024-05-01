---
title: Avserialiseringsfel för avinstallation:static-content:distribuera`
description: I den här artikeln finns en korrigering för Redis-avserialiseringsfel vid körning av "magento setup:static-content:distribuera".
exl-id: 4bc88933-3bf9-4742-b864-b82d3c1b07a9
feature: Cache, Deploy, Page Content, SCD, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Avserialiseringsfel `setup:static-content:deploy`

I den här artikeln finns en korrigering för Redis-avserialiseringsfel vid körning `magento setup:static-content:deploy`.

Körs `magento setup:static-content:deploy` orsakar Redis-felet:

```
[Exception]
Notice: unserialize(): Error at offset 0 of 1 bytes in
/var/www/domain.com/vendor/magento/module-config/App/Config/Type/System.php on line 214
```

Problemet orsakas av parallella interfereringsprocesser i Redis-anslutningen.

För att lösa `setup:static-content:deploy` i entrådsläge genom att ställa in följande miljövariabel:

```
STATIC_CONTENT_THREADS =1
```

eller, kör `setup:static-content:deploy` följt av kommandot `-j 1` (eller `--jobs=1` ).

Observera att om du inaktiverar flertrådning blir det långsammare att distribuera statiska resurser.

## Berörda versioner

* Lokal Adobe Commerce: 2.1.2 och senare
* Adobe Commerce om molninfrastruktur 2.1.2 och senare
* Redis, alla versioner

## Problem

Kör `setup:static-content:deploy` orsakar Redis-felet:

```php
)
[2017-06-02 19:57:59] Command:php ./bin/magento setup:static-content:deploy --jobs=3  en_US

[Exception]

Notice: unserialize(): Error at offset 0 of 1 bytes in /app/<domain>/vendor/magento/module-config/App/Config/Type/System.php
on line 214

.....

[CredisException]
read error on connection

[RedisException]
read error on connection

.....

[Exception]

Notice: unserialize(): Error at offset 0 of 1 bytes in /app/<domain>/vendor/magento/module-config/App/Config/Type/System.php
on line 214

.....

[RuntimeException]
Command php ./bin/magento setup:static-content:deploy --jobs=3  en_US  returned code 3
```

## Orsak

Problemet orsakas av parallella interfereringsprocesser i Redis-anslutningen.

Här finns en process i `App/Config/Type/System.php` förväntade sig ett svar för `system_defaultweb`, men fick ett svar på `system_cache_exists` som gjorts i en annan process. Se den detaljerade förklaringen i [Jason Woods&#39; post](https://github.com/magento/magento2/issues/9287#issuecomment-302362283).

## Lösning

Inaktivera parallellisering och körning `setup:static-content:deploy` i entrådsläge genom att ställa in följande miljövariabel:

```
STATIC_CONTENT_THREADS =1
```

Du kan också köra `setup:static-content:deploy` följt av kommandot `-j 1` (eller `--jobs=1`).

>[!NOTE]
>
>I entrådsläge kan den statiska innehållsdistributionsprocessen ta fyra gånger längre tid.

## Mer information

I vår utvecklardokumentation:

* [Konfigurera Redis](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/redis/config-redis.html)
* [Kommandoradsuppgradering](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html)
