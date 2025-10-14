---
title: Fel i PHP-inställningar
description: Den här artikeln innehåller lösningar på PHP-inställningsfel.
exl-id: 51fb3c95-2e25-4d86-a6cf-e08e90d097ca
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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
1. Leta reda på filen `php.ini` med följande kommando:

   ```
   bash    $ php --ini
   ```

1. Som användare med behörigheten `root` använder du en textredigerare för att öppna `php.ini` som anges av `Loaded Configuration File`.
1. Sök efter `memory_limit`.
1. Ändra det till värdet `2GB` för normal användning och felsökning.
1. Spara ändringarna i `php.ini` och avsluta textredigeraren.
1. Starta om webbservern. Exempel:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`
   * nginx (både CentOS och Ubuntu): `service nginx restart`

1. Försök installera igen.

## max-input-vars-fel på grund av stora formulär

Konfigurationer med ett stort antal butiksgranskningar, produkter, attribut och alternativ kan generera formulär som överskrider den förinställda PHP-gränsen. Om antalet skickade värden överstiger gränsen på `max-input-vars` som angetts inom `php.ini` (standardvärdet är 1000) överförs inte återstående data och dessa databasvärden uppdateras inte. När detta inträffar visas en varning i PHP-loggen:

```bash
PHP message: PHP Warning: Unknown: Input variables exceeded 1000. To increase the limit change max_input_vars in php.ini.
```

Det finns inget &quot;riktigt&quot;-värde för `max-input-vars`. Det beror på konfigurationens storlek och komplexitet. Ändra värdet i filen `php.ini` efter behov. Se [Nödvändiga PHP-inställningar](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/prerequisites/php-settings).

## xdebug maximum function nesting level error

Se [Under installationen kan du felsöka högsta antal funktionsfel på kapslingsnivån &#x200B;](/help/troubleshooting/miscellaneous/installation-xdebug-maximum-function-nesting-level-error.md).

## Fel visas när du öppnar en PHTML-mall

Feltexten är vanligtvis:

```bash
Parse error: syntax error, unexpected 'data' (T_STRING)
```

### Lösning: Ange `asp_tags = off` i php.ini

Flera mallar har syntax för att ge stöd för abstrakt nivå på mallar (använd olika mallmotorer som Twig) som är inkapslade i `<% %>` -taggar, som den här [mallen](https://github.com/magento/magento2/blob/2.0/app/code/Magento/Catalog/view/adminhtml/templates/product/edit/base_image.phtml) för att visa en produktbild:

```php
<img
    class="product-image"
    src="<%- data.url %>"
    data-position="<%- data.position %>"
    alt="<%- data.label %>" />
```

Mer information om [asp\_tags](http://php.net/manual/en/ini.core.php#ini.asp-tags).

Redigera `php.ini` och ange `asp_tags = off`. Mer information finns i [Nödvändiga PHP-inställningar](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/prerequisites/php-settings).
