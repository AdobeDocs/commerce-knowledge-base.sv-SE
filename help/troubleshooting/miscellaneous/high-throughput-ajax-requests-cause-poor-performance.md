---
title: Hög genomströmning AJAX begäranden orsakar dålig prestanda
description: I den här artikeln finns en lösning för prestandaproblem med Adobe Commerce lokalt eller Adobe Commerce på molninfrastrukturplatser på grund av en del förfrågningar om hög genomströmning som ger betydande serverbelastning och trafik.
exl-id: 68dfca8a-826c-4476-acaf-a139052b5dcc
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Hög genomströmning AJAX begäranden orsakar dålig prestanda

I den här artikeln finns en lösning för prestandaproblem med Adobe Commerce lokalt eller Adobe Commerce på molninfrastrukturplatser på grund av en del förfrågningar om hög genomströmning som ger betydande serverbelastning och trafik.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.2.x, 2.3.x
* Adobe Commerce lokal 2.2.x, 2.3.x

>[!NOTE]
>
>Problemet har åtgärdats i version 2.3.4 av både Adobe Commerce för molninfrastruktur och Adobe Commerce lokalt.

### Problem

Webbplatsen upplever en långsam prestanda på grund av höga dataflödesbegäranden, som till exempel kritiska AJAX.

### Orsak

Förfrågningar AJAX hög genomströmning omfattar förfrågningar som rör kundernas privata innehåll.

### Lösning

Det finns tre lösningar:

* [Uppgradera till version 2.3.4](https://devdocs.magento.com/cloud/project/project-upgrade.html). Om detta inte är möjligt för närvarande, [installera korrigeringsfilen som åtgärdar problemet](/help/troubleshooting/known-issues-patches-attached/performance-issues-caused-by-excessive-ajax-requests.md).
* Se till att enklare förfrågningar görs (cachelagra förfrågningar eller flytta till kundens privata innehåll).
* Minska antalet förfrågningar.

<u>Se till att enklare förfrågningar görs (cachelagra förfrågningar eller flytta till kundens privata innehåll)</u>

Om det finns AJAX förfrågningar från tredje part som aktiveras på varje sida, försöker du cachelagra förfrågningarna eller flytta dem till kundens privata innehåll. Handlaren kan göra detta genom att se till att anpassade AJAX anropas med HTTP-metoder för GET. Det kommer att göra dessa förfrågningar tillgängliga för Fastly. Om det finns anpassade AJAX som inte ska cachelagras bör de omfaktoriseras enligt funktionen för privat innehåll. För steg, se [Privat innehåll](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html) i vår dokumentation för utvecklare.

<u>Minska antalet förfrågningar</u>

* Inaktivera den beständiga kundvagnen eftersom den kan öka antalet `customer/section/load` förfrågningar. Följ stegen i [Beständiga kundvagnssökvägar](https://devdocs.magento.com/guides/v2.3/config-guide/prod/config-reference-most.html#persistent-shopping-cart-paths) i vår utvecklardokumentation för att se om kundvagnen är aktiverad.
* Om du behöver läsa in eller göra innehåll ogiltigt i `sections.xml` följer stegen i [Privat innehåll: Ovalidera privat innehåll](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html#invalidate-private-content) i vår dokumentation för utvecklare. Kontrollera att du inte använder `customerData.reload()` direkt i anpassningarna.
* Kontrollera andra POSTER AJAX förfrågningar på samma sida. Öppna utvecklarverktyget Google Chrome i webbläsaren Google Chrome. Klicka på **Nätverk** -fliken och sedan **XHR** och här finns en lista över alla AJAX från den aktuella sidan. Klicka sedan på varje begäran och i fältet Metod för begäran ska vara GET-begäran. Obs! Google Chrome används som exempel och det går även att göra detta i andra webbläsare.
* Kontrollera funktionerna i Google Tag Manager (GTM) som är en specifik AJAX. Användaren kan ta bort den här AJAX och ändra anpassningstiden med privata funktioner för att minska det totala antalet begäranden till servern.
* Kontrollera om Adobe Commerce Banner är aktiverad men inte används. Du kanske måste [Inaktivera utdata från Adobe Commerce Banner för att förbättra webbplatsens prestanda](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md).

### Relaterad läsning

Mer information om privat kundinnehåll finns på [Privat innehåll](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=ajax%20requests) i vår dokumentation för utvecklare.
