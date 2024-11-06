---
title: Okänd cache orsakar försämrad svarstid
description: I den här artikeln beskrivs hur du undviker cacheogiltigförklaring, vilket kan göra att en Adobe Commerce-butik körs långsamt.
exl-id: 7cb6a39f-923b-4acc-965d-23cf7b52c25a
feature: Cache, Catalog Management, Categories
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# Okänd cache orsakar försämrad svarstid

I den här artikeln beskrivs hur du undviker cacheogiltigförklaring, vilket kan göra att en Adobe Commerce-butik körs långsamt.

BERÖRDA PRODUKTER OCH VERSIONER:

* Adobe Commerce lokal 2.2.x, 2.3.x
* Adobe Commerce om molninfrastruktur 2.2.x, 2.3.x

## Problem

Långsam svarstid.

## Orsak

Lång svarstid kan orsakas av att cachen ogiltigförklaras (töms).

Cacheminnet används för att generera snabba svar på webbplatsbesökarnas begäran. Om det inte finns några lämpliga cachedata tillgängliga hämtar Adobe Commerce-programmet data från databasen, beräknar och sammanställer data och lagrar dem till cachelagringen. Cachegenereringsprocessen kräver ytterligare systemresurser, vilket ger en total svarstidsförsämring.

Det finns två typer av cacheminne i Adobe Commerce:

1. Intern:
   * lagrar data på servern
   * lagrar specifika data (konfiguration, produktinformation, kategoriinformation osv.)
1. Extern:
   * CDN eller lack (för Adobe Commerce i molninfrastruktur - Fast CDN)
   * lagrar redan genererade fullständiga sidor. Exempel: katalog/kategori, katalog-/produktsidor osv.

### Kontrollera om cacheminnet är ogiltigt

Du kan hitta information om ogiltiga cachetyper i filen `<install_directory>/var/log/debug.log`.

Så här gör du:

1. Öppna `<install_directory>/var/log/debug.log`
1. Sök efter meddelandet *cache\_invalidate*.
1. Kontrollera sedan den angivna taggen. Det visar vilken cache som tömdes. Du kan ha problem på grund av den ogiltiga cachen om du ser en tagg utan något särskilt enhets-ID angivet, till exempel:
   * `cat_p` - står för katalogproduktcache.
   * `cat_c` - katalogkategoricache.
   * `FPC` - helsidescache.
   * `CONFIG` - konfigurationscache.

   Att ens en av dem skulle bli flytande skulle göra webbplatsens respons långsammare. Om taggen innehåller ett enhets-ID, till exempel `category_product_1258`, skulle detta visa cachen för en viss produkt eller kategori och så vidare. Tömning av cacheminnet för en viss produkt eller kategori gör inte att svarstiden minskar avsevärt.

Följande är ett exempel på en `debug.log` som innehåller poster om att cachen `cat_p` och `category_product_15044` har tömts:

![exempel på debug.log-innehåll](assets/debug_log_sample.png)

Vanligtvis blir cachen ogiltig på grund av följande:

* Fullständig omindexering.
* Flash-cache från CLI, antingen manuellt eller med cron.

## Rekommendation

1. Undvik att tömma cacheminnet från Commerce CLI.
1. Konfigurera indexerare till **Uppdatera enligt schema** i stället för **Uppdatera vid sparläge** eftersom det senare utlöser fullständig omindexering. Mer information finns i [Hantera indexerare > Konfigurera indexerare](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers) i utvecklardokumentationen.
