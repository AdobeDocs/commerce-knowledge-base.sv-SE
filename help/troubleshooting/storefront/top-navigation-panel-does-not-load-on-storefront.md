---
title: Övre navigeringspanelen läses inte in i butiken
description: I den här artikeln finns konfigurationslösningar för ESI-problem (Varnish Edge Side Includes), där vissa sidors innehåll, vanligtvis den översta navigeringspanelen, inte visas i butiken om Varnish används för cachelagring.
exl-id: e7f9b773-1a2d-4c3b-9e1f-a1781fbc898c
feature: Categories, Site Navigation, Storefront, Variables
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Övre navigeringspanelen läses inte in i butiken

I den här artikeln finns konfigurationslösningar för ESI-problem (Varnish Edge Side Includes), där vissa sidors innehåll, vanligtvis den översta navigeringspanelen, inte visas i butiken om Varnish används för cachelagring.

## Berörda produkter och versioner

* Adobe Commerce 2.X.X
* Alla varniska versioner

## Problem

<u>Förutsättningar</u>:

Installera och konfigurera Varnish för din Adobe Commerce Store.

<u>Steg som ska återskapas</u>:

1. Gå till butiken.
1. Bläddra bland butikssidorna.

<u>Förväntade resultat</u>:

Allt innehåll och alla sidblock har lästs in.

<u>Faktiska resultat</u>:

Observera att vissa innehållsblock, som den övre navigeringspanelen med kategorier, inte läses in. Tomt utrymme visas i stället.

## Orsak

Följande orsaker kan finnas:

* ESI-inkluderingstaggar genereras med HTTPS-åtkomstprotokoll, medan varnish bara fungerar med HTTP.
* Varnish bearbetar inte ESI inuti JSON.
* Svarshuvuden är för stora för lack. De kan inte bearbetas.

## Lösning

För att lösa problemen måste du utföra ytterligare en Varnish-konfiguration och starta om Varnish.

1. Som användare med `root`-behörighet öppnar du konfigurationsfilen för spanska i en textredigerare. Se [Ändra systemkonfigurationen för lack](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/cache/config-varnish-server) i utvecklardokumentationen för mer information om var filen kan finnas för olika operativsystem.
1. I `DAEMON_OPTS variable` lägger du till `-p feature=+esi_ignore_https`, `-p  feature=+esi_ignore_other_elements`, `-p  feature=+esi_disable_xml_check`. Det här skulle se ut så här:

   ```bash
   DAEMON_OPTS="-a :6081 \    -p feature=+esi_ignore_other_elements \    -p feature=+esi_disable_xml_check \    -p feature=+esi_ignore_https \    -T localhost:6082 \    -f /etc/varnish/default.vcl \    -S /etc/varnish/secret \    -s malloc,256m"
   ```

1. Spara ändringarna och avsluta textredigeraren.
1. Öka svarsrubrikerna i VCL-konfigurationsfilen genom att öka värdena för följande parametrar: `http_resp_hdr_len`, `http_resp_size`, `workspace_backend`. Se till att de två sista har liknande värden.
1. När du ändrar detta måste du köra `service varnish restart` för att ändringarna ska börja gälla.

## Relaterad läsning

* [Konfigurera lack och din webbserver](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/cache/config-varnish-server) i utvecklardokumentationen.
* [Varnish-dokumentation](https://varnish-cache.org/docs/5.1/reference/index.html)
