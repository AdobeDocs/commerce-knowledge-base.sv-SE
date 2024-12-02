---
title: Under installationen, exception SessionHandler::read()
description: I den här artikeln finns en korrigering för ett undantagsfel **SessionHandler::read()** under Adobe Commerce-installation.
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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
>Det här felet inträffar endast i kodversioner före den 28 september 2015. Om du installerar kod som är daterad 29 september eller senare bör det här felet inte inträffa. Mer information om konfigurationsalternativ för Redis finns i [Konfigurera Redis](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/redis/config-redis) i utvecklardokumentationen. Mer information om hur du anger Redis med kommandoradsinstallationsprogrammet finns i [installationsavsnittet](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/advanced) eller [avsnittet om distributionskonfiguration](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/deployment) i utvecklardokumentationen.

## Orsak

Detta inträffar när din `session.save_handler` PHP-parameter är inställd på någon annan sessionslagring än `files` (till exempel `redis`, `memcached` och så vidare). Det här är ett känt problem som vi arbetar med att lösa.

## Lösningar:

* Uppgradera din Adobe Commerce-kod. Se [Installationshandbok > Uppdatera Adobe Commerce-programvaran](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall) i utvecklardokumentationen.
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
