---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.30'
description: Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av patcharna i [!DNL Quality Patches Tool] (QPT) v1.1.30.
exl-id: 40b1bb88-5032-4c56-ae32-99f55df12652
feature: Tools and External Services
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# Översikt [!DNL Quality Patches Tool] (QPT) v1.1.30

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av patcharna i [!DNL Quality Patches Tool] (QPT) v1.1.30.

QPT v1.1.30 innehåller följande patchar:

1. **ACSD-50336**: Korrigerar problemet där e-postmeddelanden om produktvarningar inte skickas när en produkt är tillbaka i lager eller priset ändras.
1. **ACSD-50367**: Korrigerar problemet där kundadressexport inte fungerar när ett flervalsattribut för kundadress utan värden skapas.
1. **ACSD-49877**: Korrigerar problemet där automatisk uppspelning av video inte fungerar på mobilen [!DNL Safari] när videon är länkad direkt till en fjärrvideofil och inte till en direktuppspelningstjänst.
1. **ACSD-50165**: Åtgärdar felet *Det går inte att ta bort filen. Varning!unlink: Det finns ingen sådan fil eller katalog när JS/CSS-cachen töms från administratören*.
1. **ACSD-49737**: Korrigerar problemet där en kupong felaktigt markerats som använd efter en misslyckad kortbetalning.
1. **ACSD-50814**: Åtgärdar problemet där en administratörsanvändare inte kan skapa en kreditnota.
1. **ACSD-50116**: Korrigerar problemet där en administratörsanvändare inte kan skapa en URL-omskrivning för underkategorierna nivå 3 eller lägre.
1. **ACSD-49513**: Korrigerar problemet där synkronisering av fjärrlagring misslyckas på grund av filer på 0 byte.
1. **ACSD-46683**: Korrigerar problemet där leveranspriset visas *Inte beräknat ännu*.
1. **ACSD-49129**: Korrigerar problemet där innehållsattributet ([!UICONTROL base64 image code]) returneras inte i `rest/V1/products/sku/media` API-svar för produktmedia.
1. **ACSD-50276**: Korrigerar problemet där kundregistreringsformuläret inte fungerar i butiken om ett kundattribut med flera val skapas.
1. **ACSD-50527**: Korrigerar det fel som inträffar när en sida sparas med ett tomt dynamiskt block.
1. **ACSD-49973**: Förbättrar prestanda vid hämtning av paketerade produkter via GraphQL.
1. **ACSD-5114**: Korrigerar problemet där en slumpmässig produkt försvinner från stora kataloger när asynkron indexering är aktiverat. Förbättrar prestanda för asynkron omindexering för stora kataloger.
1. **B2B-2598**: Lägger till cachelagring i `availableStores`, `countries`, `country`, `currency`och `storeConfig` GraphQL-frågor.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
