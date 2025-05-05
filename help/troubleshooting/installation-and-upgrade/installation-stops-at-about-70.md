---
title: Installationen avbryts med cirka 70 %
description: I den här artikeln finns en korrigering för när installationen stoppas vid cirka 70 %.
exl-id: 04aa3572-3c42-4565-9f7f-b4d90df96df2
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Installationen avbryts med cirka 70 %

I den här artikeln finns en korrigering för när installationen stoppas vid cirka 70 %.

## Problem

Under installationen med hjälp av installationsguiden stannar processen vid ca 70 % (med eller utan exempeldata). Inga fel visas på skärmen.

## Orsak

Vanliga orsaker till detta problem är:

* PHP-inställningen för [`max_execution_time`](http://php.net/manual/en/info.configuration.php#ini.max-execution-time)
* Timeoutvärden för nginx och varnish

## Lösning:

Ställ in följande på lämpligt sätt.

### Alla webbservrar och lack {#all-web-servers-and-varnish}

1. Leta upp `php.ini` med hjälp av en [`phpinfo.php`](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/prerequisites/optional-software)-fil.
1. Som användare med `root`-behörighet öppnar du `php.ini` i en textredigerare.
1. Leta reda på inställningen `max_execution_time`.
1. Ändra värdet till `18000`.
1. Spara ändringarna i `php.ini` och avsluta textredigeraren.
1. Starta om Apache:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

   Om du använder nginx eller Varnish fortsätter du med följande avsnitt.

### Endast nginx {#nginx-only}

Om du använder nginx använder du våra `nginx.conf.sample` eller lägger till timeout-inställningar i konfigurationsfilen för nginx-värden i avsnittet `location ~ ^/setup/index.php` enligt följande:

```php
location ~ ^/setup/index.php {
    .....................
    fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
}
```

Starta om nginx: `service nginx restart`

### Endast varniska {#varnish-only}

Om du använder lack redigerar du `default.vcl` och lägger till ett timeout-gränsvärde i `backend`-stanza enligt följande:

```php
backend default {
.....................
      .first_byte_timeout = 600s;
}
```

Starta om lack.

```php
service varnish restart
```
