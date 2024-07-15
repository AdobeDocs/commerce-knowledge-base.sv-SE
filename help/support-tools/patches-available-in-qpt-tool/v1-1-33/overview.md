---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.33'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.33.
feature: Tools and External Services
role: Admin
exl-id: df3ae5e2-7c57-4ccd-af34-eb78cc60bcf6
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.33

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som är tillgängliga i [!DNL Quality Patches Tool] (QPT) v1.1.33.

QPT v1.1.33 innehåller följande patchar:

1. **ACSD-50478**: Korrigerar databasåterställningskommandot för ett fall när DB-dumpen innehåller utlösare och ett SQL-avgränsarkommando.
1. **ACSD-50512**: Korrigerar felet: *Den hämtningsbara länken är inte relaterad till produkten. Kontrollera länken och försök igen.* som inträffar när du uppdaterar startdatumet för en hämtningsbar mellanlagringsuppdatering för produkten.
1. **ACSD-50949**: Korrigerar problemet där prisfiltret i [!UICONTROL Advanced Search] inte returnerar korrekta resultat när det används tillsammans med SKU-filtret.
1. **ACSD-51645**: Korrigerar felet som uppstod när en ny [!UICONTROL Cart Price Rule] skulle sparas om tillägget `Magento_OfflineShipping` är inaktiverat.
1. **ACSD-50895**: Korrigerar problemet där [!DNL Google Analytics] 3 GTM-taggar inte utlöses om [!DNL Google Analytics] 4 GTM inte har konfigurerats.
1. **ACSD-51102**: Korrigerar problemet där en katalogregel som tillämpas på ett stort antal produkter inte indexeras korrekt när regeln aktiveras av en schemalagd uppdatering.
1. **ACSD-50368**: Korrigerar problemet där kundens `group_id` ignoreras när en kund skapas via Async REST API eller Async Bulk REST API.
1. **ACSD-51497**: Korrigerar problemet där en kund inte kan sortera en katalogsida efter [!UICONTROL Custom Attribute] i listrutetypen.
1. **ACSD-51408**: Korrigerar problemet där orderobjektets status är felaktigt inställd på [!UICONTROL Backordered].
1. **ACSD-51735**: Korrigerar problemet där status för orderartikel felaktigt har angetts till [!UICONTROL Ordered] när produktstocken är *0*.
1. **ACSD-51792**: Korrigerar problemet där en sida inte har en inställningshändelse när [!DNL Google Tag Manager] 4 är aktiverat.
1. **ACSD-51471**: Korrigerar problemet där en administratörsanvändare inte kan spara en schemalagd uppdatering för en paketerad produkt som använder en enkel produkt som själv har en schemalagd uppdatering.
1. **ACSD-51700**: Korrigerar felet som inträffar när butiksvyer växlas på en hämtningsbar produktredigeringssida i administratören.
1. **ACSD-51120**: Korrigerar problemet där GraphQL GET begär cache inte rensas för CMS-sidor som innehåller CMS-block som uppdateras via en mellanlagringsuppdatering.
1. **ACSD-51240**: Korrigerar problemet där den överförda filen saknas om registreringen görs via företagsregistreringsformuläret.
1. **ACSD-51907**: Korrigerar problemet där en begränsad administratörsanvändare inte kan skapa en kreditnota med offlineåterbetalning.
1. **ACSD-52148**: Korrigerar problemet där inloggningen till [!UICONTROL Google V3 reCAPTCHA Admin] misslyckas ibland.
1. **ACSD-51431**: Korrigerar problemet där en indexerarstatus fungerar även om det inte finns några nya poster i ändringsloggen.
1. **ACSD-51892**: Korrigerar prestandaproblemet där konfigurationsfiler läses in flera gånger under distributionen.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
