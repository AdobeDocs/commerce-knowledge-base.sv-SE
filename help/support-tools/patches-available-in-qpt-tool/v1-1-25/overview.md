---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.25'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.25.
exl-id: 49baf8c6-0a7e-40f3-bee8-fdcab3706727
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.1.25 - översikt

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i [!DNL Quality Patches Tool] (QPT) v1.1.25.

QPT v1.1.25 innehåller följande patchar:

1. **ACSD-47292**: Korrigerar problemet där paketerade produkter som inte finns i lager inte är tillgängliga i GraphQL-svaret om *show out-of-stock-produkterna* är inställda på *Yes* .
1. **ACSD-47520**: Korrigerar problemet där kunder förlorar belöningspoäng när en kreditnota skapas.
1. **ACSD-47910**: Korrigerar problemet med saknade order, fakturor, leveranser och kreditnotor i respektive entitetsrutnät.
1. **ACSD-48044**: Korrigerar problemet där användning av flera presentkort på en enda order med flera leveranser förhindrar att beställningar görs.
1. **ACSD-48058**: Korrigerar problemet där produktprisomindexering inte fungerar om paketprodukten inte har tilldelats någon webbplats.
1. **ACSD-48234**: Korrigerar problemet där katalogsökningsresultatet visar ett felaktigt antal kategoriobjekt när alternativet *visa ur lager* är aktiverat.
1. **ACSD-48262**: Korrigerar problemet där produkter inte visas i klientdelen när inställningen *[!UICONTROL Allow All Products Per Page]* är *Ja*.
1. **ACSD-48293**: Korrigerar problemet där de sammansatta produkterna lämnar lagret när de underordnade produkter som sålts returneras till lagret.
1. **ACSD-48300**: Korrigerar problemet där en retur inte kan skapas om den konfigurerbara produkten tas bort.
1. **ACSD-48313**: Korrigerar problemet där kolumnen *configurable_variations* inte tolkas om attributvärdet innehåller ett komma. Samma parsningsalgoritm används för *additional_attributes*.
1. **ACSD-48627**: Korrigerar problemet där den konfigurerbara produkten som inte finns i lager orsakar ett fel när en GraphQL-begäran skickas för att få kundvagnsinformation.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
