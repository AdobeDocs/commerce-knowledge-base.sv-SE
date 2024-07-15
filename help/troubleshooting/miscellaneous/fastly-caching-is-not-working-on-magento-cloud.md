---
title: Snabb cachelagring fungerar inte på Adobe Commerce i molninfrastrukturen
description: Den här artikeln innehåller en korrigering för snabb cachelagring som inte fungerar på din plats. Fast är en CDN och cachningstjänst som ingår i Adobe Commerce om molninfrastrukturplaner och implementeringar. Om du vill verifiera att tillägget Snabbt fungerar eller felsöka tillägget Snabbt kan du använda kommandot curl för att visa vissa svarshuvuden. Värdena för dessa svarshuvuden anger om Fast är aktiverat och fungerar som det ska. Du kan undersöka problem ytterligare baserat på rubrikvärden och cachelagring.
exl-id: 725949e9-b69b-456f-9c56-e2163143a71e
feature: Cache, Cloud, Console, Paas
role: Developer
source-git-commit: 586a8c6340bfd2cbf773d1b009d6e106e930117d
workflow-type: tm+mt
source-wordcount: '1207'
ht-degree: 0%

---

# Snabb cachelagring fungerar inte på Adobe Commerce i molninfrastrukturen

Den här artikeln innehåller en korrigering för snabb cachelagring som inte fungerar på din plats. Fast är en CDN och cachningstjänst som ingår i Adobe Commerce om molninfrastrukturplaner och implementeringar. Om du vill verifiera att tillägget Snabbt fungerar eller felsöka tillägget Snabbt kan du använda kommandot curl för att visa vissa svarshuvuden. Värdena för dessa svarshuvuden anger om Fast är aktiverat och fungerar som det ska. Du kan undersöka problem ytterligare baserat på rubrikvärden och cachelagring.

Den här informationen hjälper dig att verifiera och testa snabbmeddelandehuvuden för dina aktiva webbplats- och ursprungsservrar.

## Berörda versioner

* Adobe Commerce i molninfrastruktur
* Snabbt 1.2.27 och senare

## Problem

Cachelagring fungerar kanske inte för den publicerade webbplatsen, produktionen eller mellanlagringsmiljön.

## Orsak

Vanligtvis fungerar inte konfigurationer, felaktiga autentiseringsuppgifter eller Adobe Commerce-tillägg som inte stöds för Snabb cachelagring. Om du ställer in snabbt på fel sätt eller använder ett tillägg som inte stöds för att ta bort rubriker, fungerar inte cachelagring snabbt.

## Testa med kommandon och kontrollera svarsrubriker

### Testa med kommandot Utfall

Kontrollera först om det finns rubriker med ett digeringskommando till URL:en. I ett terminalprogram anger du digering `<url>` för att verifiera visningen av snabbtjänster i rubrikerna. Mer information om ytterligare felsökningstester finns i Fastly&#39;s [Testing innan du ändrar DNS](https://docs.fastly.com/guides/basic-configuration/testing-setup-before-changing-domains).

Exempel:

* Live-webbplats: `dig http[s]://<your domain>`
* Mellanlagring: `dig http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud`
* Produktion: `dig http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud`

### Testa med rullning, kommando

Använd sedan ett bol-kommando för att kontrollera att det finns X-Magento-taggar och ytterligare rubrikinformation. Kommandoformatet skiljer sig åt för Förproduktion och Förproduktion.

Om du vill ha mer information om de här kommandona går du snabbt förbi när du injicerar `-H "host:URL"`, ersätter med ursprung till anslutningspunkten (CNAME-information från ditt OneDrive-kalkylblad), `-k` ignorerar SSL och `-v` ger utförliga svar. Om rubrikerna visas korrekt kontrollerar du den publicerade webbplatsen och verifierar rubrikerna igen.

* Om det uppstår rubrikproblem när du stöter direkt på de ursprungliga servrarna utan att passera snabbt, kan du få problem med koden, tilläggen eller infrastrukturen.
* Om du inte råkar ut för några fel direkt på de ursprungliga servrarna, men det saknas rubriker som fastnar i den aktiva domänen, kan du få snabba fel.

Kontrollera först din **aktiva webbplats** för att verifiera svarsrubrikerna. Kommandot går igenom tillägget Snabb för att ta emot svar. Om du inte får rätt rubriker bör du testa de ursprungliga servrarna direkt. Det här kommandot returnerar värdena för rubrikerna `Fastly-Magento-VCL-Uploaded` och `X-Cache`.

1. Ange följande kommando i en terminal för att testa URL:en för den aktiva webbplatsen:

   ```
   curl http://<live URL> -vo /dev/null -HFastly-Debug:1 [--resolve]
   ```

   Använd bara `--resolve` om din live-URL inte har konfigurerats med DNS och du inte har någon statisk rutt angiven. Exempel:

   ```
   curl http://www.mymagento.biz -vo /dev/null -HFastly-Debug:1
   ```

1. Kontrollera svarsrubrikerna för att säkerställa att Fast fungerar. Utdata för det här kommandot liknar utdata för rullande materiel och produktion. Du kan till exempel se de returnerade unika rubrikerna med det här kommandot:

   ```
   < Fastly-Magento-VCL-Uploaded: yes    < X-Cache: HIT, MISS
   ```

Så här testar du **Förproduktion**:

```
curl http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Så här testar du **produktionsbelastningsutjämnaren**:

```
curl http[s]://<your domain>.c.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Så här testar du **produktionsstartnod** :

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

En nod för direkt origo:

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Om du t.ex. har en publik URL-adress www.mymagento.biz, anger du ett kommando som liknar följande för att testa produktionsplatsen:

```
curl -k https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud -H 'Host: www.mymagento.biz' -vo /dev/null -HFastly-Debug:1
```

### Kontrollera svarsrubriker

* Kontrollera returnerade svarshuvuden och värden:
* Fast-Magento-VCL-Uploaded ska finnas
* X-Magento-Tags ska returneras
* Fasta modulaktiverade ska vara antingen Ja eller snabbtilläggets versionsnummer
* X-Cache ska vara antingen HIT eller HIT, HIT
* x-cache-hits ska vara 1,1
* Cache-Control: max-age ska vara större än 0
* Pragma ska vara cache

I följande exempel visas de korrekta värdena för Pragma, X-Magento-Tags och Fast-Module-Enabled.

Utdata för böjkommandon kan vara långa. Här följer en sammanfattning:

```
* STATE: INIT => CONNECT handle 0x600057800; line 1402 (connection #-5000)
* Rebuilt URL to: https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud/
* Added connection 0. The cache now contains 1 members
* Trying 192.0.2.31...
* STATE: CONNECT => WAITCONNECT handle 0x600057800; line 1455 (connection #0)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                             Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* Connected to www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud (54.229.163.31) port 443 (#0)
* STATE: WAITCONNECT => SENDPROTOCONNECT handle 0x600057800; line 1562 (connection #0)
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* ALPN, offering h2

  ... portion omitted for brevity ...

< Set-Cookie: mage-messages=%5B%5D; expires=Wed, 22-Nov-2017 17:39:58 GMT; Max-Age=31536000; path=/
< Pragma: cache
< Expires: Wed, 23 Nov 2016 17:39:56 GMT
< Cache-Control: max-age=86400, public, s-maxage=86400, stale-if-error=5, stale-while-revalidate=5
< X-Magento-Tags: cb_welcome_popup store cb cb_store_info_mobile cb_header_promotional_bar cb_store_info cb_discount-promo-bar cpg_2 cb_83 cb_81 cb_84 cb_85 cb_86 cb_87 cb_88 cb_89 p5646 catalog_product p5915 p6040 p6197 p6227 p7095 p6109 p6122 p6331 p7592 p7651 p7690
< Fastly-Module-Enabled: yes
< Strict-Transport-Security: max-age=31536000
    < Content-Security-Policy: upgrade-insecure-requests
< X-Content-Type-Options: nosniff
< X-XSS-Protection: 1; mode=block
< X-Frame-Options: SAMEORIGIN
< X-Platform-Server: i-dff64b52
<
* STATE: PERFORM => DONE handle 0x600057800; line 1955 (connection #0)
* multi_done
  0     0    0     0    0     0      0      0 --:--:--  0:00:02 --:--:--     0
* Connection #0 to host www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud left intact
```

## Lös

### Snabbmodulsaktiverad finns inte

Om du inte får ett ja för snabbmodulsaktiverad i svarshuvuden måste du kontrollera att snabbmodulen är installerad och markerad.

Kontrollera konfigurationen i Commerce Admin för varje miljö om du vill kontrollera att Fast är aktiverat i Förproduktion:

1. Logga in på Admin Console for Staging and Production med URL:en /admin (eller den ändrade Admin URL:en).
1. Navigera till Lager > Konfiguration > Avancerat > System. Bläddra och klicka på Cacheminnet för helsida.
1. Kontrollera att Snabbt CDN är markerat.
1. Klicka på Snabb konfiguration. Kontrollera att du har angett snabb service-ID och snabb API-token (dina snabbinloggningsuppgifter). Kontrollera att du har angett rätt autentiseringsuppgifter för mellanlagrings- och produktionsmiljön. Klicka på Testa autentiseringsuppgifter om du vill ha hjälp.
1. Redigera din Composer.json och kontrollera att Fasty-modulen ingår i versionen. Den här filen innehåller alla moduler listade med versioner.

   * I avsnittet &quot;Kräv&quot; ska du ha &quot;fastly/magento2&quot;: `<version number>`
   * Under Databaser bör du ha:

   ```
   "fastly-magento2": {    "type": "vcs",    "url": "https://github.com/fastly/fastly-magento2.git"    }
   ```

1. Om du använder Configuration Management bör du ha en konfigurationsfil. Redigera filen app/etc/config.app.php (2.0, 2.1) eller app/etc/config.php (2.2) och kontrollera att inställningen `'Fastly_Cdn' => 1` är korrekt. Inställningen ska inte vara `'Fastly_Cdn' => 0` (d.v.s. inaktiverad).Om du aktiverade snabbt tar du bort konfigurationsfilen och kör kommandot bin/magento magento-cloud:scd-dump för att uppdatera. En genomgång av den här filen finns i [Exempel på hantering av systemspecifika inställningar](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html#manage-the-system-specific-configuration) i konfigurationshandboken.

Om modulen inte är installerad måste du installera i en [integreringsmiljö](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) -gren och distribuera den till Förproduktion och produktion. Se [Konfigurera snabbt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) för instruktioner i Commerce om Cloud Infrastructure Guide.

### Fast-Magento-VCL-Uploaded finns inte

Under installation och konfiguration bör du ha laddat upp Snabbt VCL. Det här är de grundläggande VCL-kodfragmenten från snabbmodulen, inte anpassade VCL-kodfragment som du skapar. Instruktioner finns i [Överför snabbt VCL-kodfragment](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upload-vcl-to-fastly) i Commerce on Cloud Infrastructure Guide.

### X-Cache innehåller MISS

Om X-Cache är antingen HIT, MISS eller MISS, MISS, anger du samma curl-kommando igen för att säkerställa att sidan inte nyligen har avlägsnats från cachen.

Om du får samma resultat kan du använda rullningskommandona och verifiera svarshuvudena:

* Pragma är cache
* X-Magento-taggar finns
* Cache-Control: max-age är större än 0

Om problemet kvarstår är det troligt att ett annat tillägg återställer dessa rubriker. Upprepa följande procedur i Förproduktion för att inaktivera tillägg för att hitta vilket som orsakar problemet. När du har hittat de tillägg som orsakar problemet måste du inaktivera tilläggen i produktionen.

1. Följ stegen i avsnittet [Hantera tillägg](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html?lang=en#manage-extensions) i guiden för molninfrastruktur för att inaktivera tilläggen.
1. När du har inaktiverat tilläggen går du till **[!UICONTROL System]** > **[!UICONTROL Tools]** > **[!UICONTROL Cache Management]**.
1. Klicka på **[!UICONTROL Flush Magento Cache]**.
1. Aktivera nu ett tillägg i taget, spara konfigurationen och tömma cachen.
1. Testa att rulla kommandona och verifiera svarsrubrikerna.
1. Upprepa steg 4 och 5 för att aktivera och testa vändkommandona. När snabbrubrikerna inte längre visas har du hittat tillägget som orsakar problem med Snabbt.

När du isolerar det tillägg som återställer snabbrubriker kontaktar du tilläggsutvecklaren för ytterligare hjälp. Vi kan inte tillhandahålla korrigeringar eller uppdateringar för tilläggsutvecklare från tredje part som arbetar med Fast-cachning.

## Mer information i vår utvecklardokumentation:

* [Om snabbt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)
* [Konfigurera snabbt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)
* [Anpassade VCL-kodfragment snabbt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html)
