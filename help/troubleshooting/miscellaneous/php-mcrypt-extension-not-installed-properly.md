---
title: PHP-krypteringstillägget har inte installerats korrekt
description: PHP-krypteringstillägget har inte installerats korrekt
exl-id: 1010349e-6631-4a05-8883-5cc903d67534
feature: Extensions, Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# PHP-krypteringstillägget har inte installerats korrekt

>[!WARNING]
>
>OBS! Krypteringsbiblioteksfunktionen var [borttagen från PHP 7.1 och togs bort från PHP 7.2](https://www.php.net/manual/en/intro.mcrypt.php).

## Detalj

Följande fel kan uppstå:

```php
exception 'Exception' with message 'PHP Warning: [PHP](https://glossary.magento.com/php) Startup: Unable to load dynamic [library](https://glossary.magento.com/library) '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory
```

```php
Installing data fixtures:
/usr/bin/php -f '/Users/username/www/magento/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/Users/username/www/magento' 2>&1
[ERROR] [exception](https://glossary.magento.com/exception) 'Exception' with message '
Fatal error: Uncaught exception 'Exception' with message 'Module 'Magento_Core' depends on 'mcrypt' PHP [extension](https://glossary.magento.com/extension) that is not loaded.'
```

```php
======================================================================
   The application has thrown an exception!
======================================================================
 Magento\Framework\Exception
 Command returned non-zero exit code:
`/usr/bin/php5 -f '/var/www/magento2/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/var/www/magento2' 2>&1`
```

## Beskrivning

I synnerhet på utvecklingssystem som innehåller en &quot;stack&quot; av typen Linux/Apache/MySQL/PHP (LAMP) som är åtskild från operativsystemet, är det möjligt att mcrypt antingen inte är installerat alls eller att det är installerat i LAMP-stackens sökväg men inte operativsystemets sökväg.

Därför kan inte Adobe Commerce installationsprogram hitta tillägget och installationen misslyckas.

## Förslag

Kontrollera om krypteringstillägget har lästs in på något av följande sätt:

* Konfigurera en [phpinfo.php](http://kb.mediatemple.net/questions/764/How+can+I+create+a+phpinfo.php+page%3F#gs)-fil i webbserverns rotkatalog och granska utdata i en webbläsare.
* Kör följande kommando:    `$ php -r "phpinfo();" | grep mcrypt`

Om mcrypt är *inte* installerat visas meddelanden som liknar följande:

```php
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
```

I vissa fall kanske du måste installera Adobe Commerce-programvaran från [kommandoraden](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli.html) och ange den fullständiga sökvägen till den LAMP-stack som har kryptering installerad.
