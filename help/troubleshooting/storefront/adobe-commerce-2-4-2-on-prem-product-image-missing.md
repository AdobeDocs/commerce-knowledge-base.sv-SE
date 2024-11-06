---
title: "Adobe Commerce lokal 2.4.2: produktbild saknas"
description: I den här artikeln beskrivs ett känt problem med Adobe Commerce lokalt 2.4.2 där produktbilden inte överförs till produktsidan. Problemet är planerat att åtgärdas i en framtida version efter version 2.4.3. Det finns ingen tillgänglig lösning för tillfället, men som en tillfällig lösning kan du inaktivera Nginx för att ändra storlek på bilder.
exl-id: c4d9240e-5df5-4eab-bb4e-1f06f9bd3a1e
feature: Iaas, Products, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Adobe Commerce lokal 2.4.2: produktbild saknas

I den här artikeln beskrivs ett känt problem med Adobe Commerce lokalt 2.4.2 där produktbilden inte överförs till produktsidan. Problemet är planerat att åtgärdas i en framtida version efter version 2.4.3. Det finns ingen tillgänglig lösning för tillfället, men som en tillfällig lösning kan du inaktivera Nginx för att ändra storlek på bilder.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.4.2

## Problem

Produktbilden sparas i `s3`-hakparken, men synkroniseras inte tillbaka till katalogen `pub/media`. Problemet uppstår bara när du använder båda:

* Webbplatsaktiverad Nginx för att ändra storlek på bilder
* AWS `s3` som medielagring

<u>Förutsättningar</u>:

Adobe Commerce installerat med Nginx.

<u>Steg som ska återskapas</u>:

1. Konfigurera Adobe Commerce att använda AWS `s3` som medielagring.
1. Konfigurera Nginx med konfigurationsfilen `nginx.conf.sample` som finns i Adobe Commerce installationskatalog och ett virtuellt Nginx-värdsystem. Se [Konfigurera Nginx](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/web-server/nginx) i utvecklardokumentationen.
1. Skapa en enkel produkt med en produktbild.
1. Nginx har en okommenterad konfiguration för storleksändring av bilder i `nginx.conf.sample` som den här:

```conf
load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
location /media/ {
    location ~* ^/media/catalog/.* {
        set $width "-";
        set $height "-";
        if ($arg_width != '') {
            set $width $arg_width;
        }
        if ($arg_height != '') {
            set $height $arg_height;
        }
        image_filter resize $width $height;
        image_filter_jpeg_quality 90;
    }
```

<u>Förväntade resultat</u>:

Produktbilden överförs till produktsidan.

<u>Faktiska resultat</u>:

Produktbilden överförs inte till produktsidan.

## Tillfällig lösning

Inaktivera Nginx om du vill ändra storlek på bilder.
