---
title: Fel i PHP-inställningar
description: Den här artikeln innehåller lösningar på PHP-inställningsfel.
exl-id: 51fb3c95-2e25-4d86-a6cf-e08e90d097ca
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Fel i PHP-inställningar

Den här artikeln innehåller lösningar på PHP-inställningsfel.

## PHP-minnesbegränsningsfel

Med beredskapskontrollerna ser du till att du har minst 1 GB minne reserverat för PHP-processer. Den här inställningen bör vara tillräcklig för de flesta installationer, inklusive installation av valfria exempeldata. Vi rekommenderar dock minst 2 GB för felsökning.

Så här ökar du PHP-minnesgränsen:

1. Logga in på din Adobe Commerce-server.
1. Hitta `php.ini` med följande kommando:

   ```
   bash    $ php --ini
   ```

1. Som användare med `root` behörighet, använd en textredigerare för att öppna `php.ini` anges av `Loaded Configuration File`.
1. Sök `memory_limit`.
1. Ändra det till värdet `2GB` för normal användning och felsökning.
1. Spara ändringarna i `php.ini` och avsluta textredigeraren.
1. Starta om webbservern. Exempel:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`
   * nginx (både CentOS och Ubuntu): `service nginx restart`

1. Försök installera igen.

## max-input-vars-fel på grund av stora formulär

Konfigurationer med ett stort antal butiksgranskningar, produkter, attribut och alternativ kan generera formulär som överskrider den förinställda PHP-gränsen. Om antalet skickade värden överstiger `max-input-vars` gräns angiven inom `php.ini` (standard är 1000), återstående data överförs inte och dessa databasvärden uppdateras inte. När detta inträffar visas en varning i PHP-loggen:

```terminal
PHP message: PHP Warning: Unknown: Input variables exceeded 1000. To increase the limit change max_input_vars in php.ini.
```

Det finns inget&quot;proper&quot;-värde för `max-input-vars`; beror på hur stor och komplex konfigurationen är. Ändra värdet i `php.ini` vid behov. Se [Nödvändiga PHP-inställningar](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html).

## xdebug maximum function nesting level error

Se [Vid installation, xdebug fel på högsta funktionsnivå](/help/troubleshooting/miscellaneous/installation-xdebug-maximum-function-nesting-level-error.md).

## Fel visas när du öppnar en PHTML-mall

Feltexten är vanligtvis:

```terminal
Parse error: syntax error, unexpected 'data' (T_STRING)
```

### Lösning: Ange `asp_tags = off` in php.ini

Flera mallar har syntax för att ge support på abstrakt nivå på mallar (använd olika mallar som Twig) som är insvepta `<% %>` taggar, som detta [mall](https://github.com/magento/magento2/blob/2.0/app/code/Magento/Catalog/view/adminhtml/templates/product/edit/base_image.phtml) för att visa en produktbild:

```php
<img
    class="product-image"
    src="<%- data.url %>"
    data-position="<%- data.position %>"
    alt="<%- data.label %>" />
```

Mer information om [asp\_tags](http://php.net/manual/en/ini.core.php#ini.asp-tags).

Redigera `php.ini` och ange `asp_tags = off`. Mer information finns i [Nödvändiga PHP-inställningar](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html).
