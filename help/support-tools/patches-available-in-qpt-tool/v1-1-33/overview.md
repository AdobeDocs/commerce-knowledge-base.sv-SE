---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.33'
description: Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av patcharna i [!DNL Quality Patches Tool] (QPT) v1.1.33.
feature: Tools and External Services
role: Admin
exl-id: df3ae5e2-7c57-4ccd-af34-eb78cc60bcf6
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Översikt [!DNL Quality Patches Tool] (QPT) v1.1.33

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av patcharna i [!DNL Quality Patches Tool] (QPT) v1.1.33.

QPT v1.1.33 innehåller följande patchar:

1. **ACSD-50478**: Korrigerar databasåterställningskommandot för ett fall när DB-dumpen innehåller utlösare och ett SQL-avgränsarkommando.
1. **ACSD-50512**: Åtgärdar felet: *Den nedladdningsbara länken är inte relaterad till produkten. Kontrollera länken och försök igen.*  som inträffar när du uppdaterar startdatumet för en hämtningsbar mellanlagringsuppdatering för produkten.
1. **ACSD-50949**: Korrigerar problemet där prisfiltret [!UICONTROL Advanced Search] returnerar inte korrekta resultat när de används tillsammans med SKU-filtret.
1. **ACSD-51645**: Åtgärdar det fel som genereras när en ny sparas [!UICONTROL Cart Price Rule] om tillägget `Magento_OfflineShipping` är inaktiverat.
1. **ACSD-50895**: Åtgärdar problemet där [!DNL Google Analytics] 3 GTM-taggar aktiveras inte om [!DNL Google Analytics] 4 GTM är inte konfigurerat.
1. **ACSD-51102**: Korrigerar problemet där en katalogregel som tillämpas på ett stort antal produkter inte indexeras korrekt när regeln aktiveras av en schemalagd uppdatering.
1. **ACSD-50368**: Korrigerar problemet där kunden `group_id` ignoreras när en kund skapas via Async REST API eller Async Bulk REST API.
1. **ACSD-51497**: Korrigerar problemet där en kund inte kan sortera en katalogsida efter [!UICONTROL Custom Attribute] i listrutetypen.
1. **ACSD-51408**: Korrigerar problemet där orderartikelns status är felaktigt inställd på [!UICONTROL Backordered].
1. **ACSD-51735**: Korrigerar problemet där orderartikelns status är felaktigt inställd på [!UICONTROL Ordered] när produktlagret är *0*.
1. **ACSD-51792**: Korrigerar ett problem där en sida inte har en inställningshändelse när [!DNL Google Tag Manager] 4 är aktiverat.
1. **ACSD-51471**: Korrigerar problemet där en administratörsanvändare inte kan spara en schemalagd uppdatering för en paketerad produkt som använder en enkel produkt som själv har en schemalagd uppdatering.
1. **ACSD-51700**: Åtgärdar det fel som inträffar när butiksvyer växlas på en nedladdningsbar produktredigeringssida i administratören.
1. **ACSD-51120**: Korrigerar problemet där GraphQL GET inte rensar cache för CMS-sidor som innehåller CMS-block som uppdateras via en mellanlagringsuppdatering.
1. **ACSD-51240**: Korrigerar problemet där den överförda filen saknas om registreringen görs via företagsregistreringsformuläret.
1. **ACSD-51907**: Korrigerar problemet där en begränsad administratörsanvändare inte kan skapa en kreditnota med en offlineåterbetalning.
1. **ACSD-52148**: Åtgärdar problemet där [!UICONTROL Google V3 reCAPTCHA Admin] inloggningen misslyckas då och då.
1. **ACSD-51431**: Korrigerar problemet där en indexerarstatus fungerar även om det inte finns några nya poster i ändringsloggen.
1. **ACSD-51892**: Korrigerar prestandaproblemet där konfigurationsfiler läses in flera gånger under distributionen.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
