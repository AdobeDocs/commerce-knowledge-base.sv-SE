---
title: Åtgärda ett ogiltigt förskjutningsfel
description: I den här artikeln finns en lösning för när du i Adobe Commerce 2.1 eller senare får ett felmeddelande om att en ny produkt har skapats i Commerce Admin att åtgärdas.
exl-id: 62d16d3c-7f4b-45e9-ae4b-fe2b58cc3620
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Åtgärda ett ogiltigt förskjutningsfel

I den här artikeln finns en lösning för när du i Adobe Commerce 2.1 eller senare får ett felmeddelande om att en ny produkt har skapats i Commerce Admin att åtgärdas.

I Adobe Commerce 2.1 och senare kan följande fel visas när du skapar en ny produkt i Commerce Admin:

```text
Warning: Illegal string offset 'is_in_stock' in [...]/vendor/
magento/module-catalog-inventory/Ui/DataProvider/Product/Form/
Modifier/AdvancedInventory.php on line 87
```

## Detalj

I Adobe Commerce 2.1 och senare används PHP-kodkommentarer i valideringsanropet `getDocComment` i metoden [`getExtensionAttributes`](https://github.com/magento/magento2/blob/2.3/lib/internal/Magento/Framework/Api/ExtensionAttributesFactory.php#L64-L73) i `Magento\Framework\Api\ExtensionAttributesFactory.php`.

Om du har aktiverat PHP OPcache (vilket vi rekommenderar) visas det här felet eftersom inställningen [`opcache.save_comments`](http://php.net/manual/en/opcache.configuration.php#ini.opcache.save_comments) är inaktiverad som standard.

## Tillfällig lösning

Du löser problemet genom att leta upp dina inställningar för OPCache-konfigurationen och aktivera `opcache.save_comments` enligt följande:

### Steg 1: Leta reda på din OPCache-konfiguration

#### Så här hittar du konfigurationsinställningar för OPCache:

Inställningarna för PHP OPcache finns vanligtvis antingen i `php.ini` eller `opcache.ini`. Platsen kan vara beroende av operativsystemet och PHP-versionen. Konfigurationsfilen för OPCache kan ha ett `[opcache]`-avsnitt eller inställningar som `opcache.enable`.

Använd följande riktlinjer för att hitta den:

* Apache-webbserver:<br>

För Ubuntu med Apache finns inställningarna för OPcache vanligtvis i `php.ini`.<br>
För CentOS med Apache eller nginx finns OPcache-inställningarna vanligtvis i `/etc/php.d/opcache.ini` .<br>
Om inte, använder du följande kommando för att hitta den:

```bash
    $ sudo find / -name 'opcache.ini'
```

* nginx-webbserver med PHP-FPM: `/etc/php5/fpm/php.ini`.

Om du har fler än en `opcache.ini` ändrar du alla.


### Steg 2: Aktivera `opcache.save_comments`

1. Öppna konfigurationsfilen för OPCache i en textredigerare.
1. Leta reda på `opcache.save_comments` och avkommentera den om det behövs.
1. Kontrollera att värdet är `1`.
1. Spara ändringarna och avsluta textredigeraren.
1. Starta om webbservern:

   * Apache, Ubuntu: `service apache2 restart`
   * Apache, CentOS: `service httpd restart`
   * nginx, Ubuntu och CentOS: `service nginx restart`

1. Generera om DI-konfiguration och alla saknade klasser som kan genereras automatiskt:

```bash
    $ bin/magento setup:di:compile`
```
