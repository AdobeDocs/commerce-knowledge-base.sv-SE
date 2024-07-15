---
title: Under installationen, exception SessionHandler::read()
description: "Den här artikeln innehåller en korrigering för ett undantag **SessionHandler::read()**-fel under Adobe Commerce-installation."
source-git-commit: 5cec04f8c4f80d34fc26b06eb929960ce21e2dc0
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# Under installationen, exception SessionHandler::read()

I den här artikeln finns en korrigering för undantaget **SessionHandler::read()** vid installation av Adobe Commerce.

## Problem

I det sista steget av Adobe Commerce-installationen visas följande undantag:

```temrinal
exception 'Exception' with message 'Warning: SessionHandler::read():
open(..) failed: No such file or directory (2) ../magento2/lib/internal/Magento/Framework/Session/SaveHandler.php on line 74'
in ../magento2/lib/internal/Magento/Framework/App/ErrorHandler.php:67
```

>[!NOTE]
>
>Det här felet inträffar endast i kodversioner före den 28 september 2015. Om du installerar kod som är daterad 29 september eller senare bör det här felet inte inträffa. Mer information om konfigurationsalternativ för Redis finns i [Konfigurera Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html) i utvecklardokumentationen. Mer information om hur du anger Redis med kommandoradsinstallationsprogrammet finns i [installationsavsnittet](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-install.html) eller [avsnittet om distributionskonfiguration](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-deployment.html#instgde-cli-subcommands-configphp) i utvecklardokumentationen.

## Orsak

Detta inträffar när din `session.save_handler` PHP-parameter är inställd på någon annan sessionslagring än `files` (till exempel `redis`, `memcached` och så vidare). Det här är ett känt problem som vi arbetar med att lösa.

## Lösningar:

* Uppgradera din Adobe Commerce-kod. Se [Installationshandbok > Uppdatera Adobe Commerce-programvaran](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-uninstall.html#instgde-install-magento-update) i utvecklardokumentationen.
* Använd följande lösning med befintlig kod:

## Hitta `php.ini` {#locate-php-ini}

Leta reda på `php.ini` genom att ange följande kommando:

```php
php -i | grep "Loaded Configuration File"
```

Typiska platser är:

* Ubuntu: `/etc/php5/cli/php.ini`
* CentOS: `/etc/php.ini`

## Tillfällig lösning {#workaround}

1. Som användare med `root`-behörighet öppnar du `php.ini` i en textredigerare.
1. Hitta `session.save_handler`
1. Gör något av följande:
   * Så här kommenterar du det:

     ```php
     ;session.save_path = <path>
     ```

   * Så här anger du en filsystemsökväg:

     ```php
     session.save_handler = files
     ```
