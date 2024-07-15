---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.0.13'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.0.13.
exl-id: c25d2926-2137-4a55-abb2-8c0cbff184c9
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.13 - översikt

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i [!DNL Quality Patches Tool] (QPT) v1.0.13.

QPT v1.0.13 innehåller följande patchar:

1. **MCP-87**: Förbättrad indexeringstid för kategoriprodukter och börsindexerare för stora profiler.
1. **MDVA-13203**: Korrigerar problemet där felet *Integritetsbegränsningen search_tmp_ table* visas efter en fullständig omindexering.
1. **MDVA-19391**: Korrigerar problemet där `analytics_collect_data` genererar ett fel på grund av NULL-beskrivningsposter i tabellen `catalog_category_entity_text`.
1. **MDVA-20376**: Korrigerar problemet med *Ingen sådan entitet med customerId = 1* fel i `exception.log` för inloggade kunder efter orderplacering.
1. **MDVA-22150**: Korrigerar problemet där kunder med en konfigurerbar produkt i kundvagn och en kupong som används inte kan logga in om den konfigurerbara produkten är inaktiverad i administratören.
1. **MDVA-23426**: Korrigerar problemet där e-postmeddelanden från Adobe Commerce innehåller en tom brödtext med innehåll som läggs till som en bifogad fil.
1. **MDVA-23764**: Korrigerar felet i `JsFooterPlugin.php` som påverkar visningen av dynamiska block.
1. **MDVA-30858**: Korrigerar problemet med att [!DNL PayPal] kvittningsrapporter inte är tillgängliga under **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL PayPal]** kvittning som förväntat.
1. **MDVA-32545**: Korrigerar problemet där fakturor inte skickas ut automatiskt när order skapas från administratören.
1. **MDVA-32714**: Korrigerar problemet där kundgruppspriset inte fungerar i GraphQL-produktfrågan.
1. **MDVA-33106**: Korrigerar det problem där de tidsplanerade produktändringarna raderas efter att cron `run`-kommandot har körts.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
