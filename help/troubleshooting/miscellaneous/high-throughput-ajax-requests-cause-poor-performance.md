---
title: Hög genomströmning för AJAX-begäranden orsakar dålig prestanda
description: I den här artikeln finns en lösning för prestandaproblem med Adobe Commerce lokalt eller Adobe Commerce på molninfrastrukturplatser på grund av en del förfrågningar om hög genomströmning som ger betydande serverbelastning och trafik.
exl-id: 68dfca8a-826c-4476-acaf-a139052b5dcc
feature: Cache
role: Developer
source-git-commit: b6e44e106dcc546949459a79c0f2e49b87e1d376
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Hög genomströmning för AJAX-begäranden orsakar dålig prestanda

I den här artikeln finns en lösning för prestandaproblem med Adobe Commerce lokalt eller Adobe Commerce på molninfrastrukturplatser på grund av en del förfrågningar om hög genomströmning som ger betydande serverbelastning och trafik.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.2.x, 2.3.x
* Adobe Commerce lokal 2.2.x, 2.3.x

>[!NOTE]
>
>Problemet har åtgärdats i version 2.3.4 av både Adobe Commerce för molninfrastruktur och Adobe Commerce lokalt.

### Problem

Webbplatsen upplever en långsam prestanda på grund av höga dataflödesbegäranden, som viktiga AJAX-förfrågningar.

### Orsak

AJAX förfrågningar med stort genomflöde omfattar förfrågningar som rör kundernas privata innehåll.

### Lösning

Det finns tre lösningar:

* [Uppgradera till version 2.3.4](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version).
* Se till att enklare förfrågningar görs (cachelagra förfrågningar eller flytta till kundens privata innehåll).
* Minska antalet förfrågningar.

<u>Kontrollera ljusare förfrågningar (cacheförfrågningar eller flytta till kundens privata innehåll)</u>

Om det finns AJAX-förfrågningar från tredje part som aktiveras på varje sida, försöker du cachelagra förfrågningarna eller flytta dem till kundens privata innehåll. Handlaren kan göra detta genom att se till att anpassade AJAX-förfrågningar anropas med GET HTTP-metoder. Det kommer att göra dessa förfrågningar tillgängliga för Fastly. Om det finns anpassade AJAX-begäranden som inte ska cachas, bör de omfaktoriseras enligt funktionen för privat innehåll. Anvisningar finns i [Privat innehåll](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) i utvecklardokumentationen.

<u>Minska antalet förfrågningar</u>

* Inaktivera den beständiga kundvagnen eftersom den kan öka antalet `customer/section/load`-begäranden. Följ stegen i [Beständiga kundvagnssökvägar](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/paths/config-reference-general) i vår utvecklardokumentation för att se om beständig kundvagn är aktiverad.
* Om du behöver läsa in eller göra innehåll ogiltigt i `sections.xml` följer du stegen i [Privat innehåll: Gör privat innehåll ogiltigt](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content) i utvecklardokumentationen. Kontrollera att du inte använder metoden `customerData.reload()` direkt i dina anpassningar.
* Kontrollera andra POST AJAX-begäranden på samma sida. Öppna Google Chrome Developer Tool i Google Chrome webbläsare. Klicka på fliken **Nätverk** och sedan på fliken **XHR** så visas en lista över alla AJAX-begäranden från den aktuella sidan. Klicka sedan på varje begäran och i fältet Metod för begäran ska vara GET-begäran. Obs! Google Chrome används som exempel och det går även att göra detta i andra webbläsare.
* Kontrollera funktionerna i Google Tag Manager (GTM) som är en specifik AJAX-förfrågan. Användaren kan ta bort denna AJAX och omfaktorisera anpassningen med privata funktioner för att minska det totala antalet begäranden till servern.
* Kontrollera om Adobe Commerce Banner är aktiverad men inte används. Du kan behöva [Inaktivera Adobe Commerce Banner-utdata för att förbättra webbplatsens prestanda](https://experienceleague.adobe.com/sv/docs/experience-cloud-kcs/kbarticles/ka-26909).

### Relaterad läsning

Mer information om privat kundinnehåll finns i [Privat innehåll](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) i utvecklardokumentationen.
