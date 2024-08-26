---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.50'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.50.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: f62cf4284d7bb99a1ab58df676dfff726c34d327
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.50

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i [!DNL Quality Patches Tool] (QPT) v1.1.50.

QPT v1.1.50 innehåller följande patchar:

1. **ACSD-59280**: Korrigerar problemet där felet *Anrop till undefined method ReflectionUnionType::getName()* inträffar när 2.4.4-pX-versioner installeras.
1. **ACSD-45049**: Korrigerar problemet där kundens *[!UICONTROL Is required]* attributinställning inte fungerar som den ska per webbplats i Admin.
1. **ACSD-46938**: Korrigerar problemet med prestandan hos DB-utlösare som återskapas under `setup:upgrade`.
1. **ACSD-48210**: Korrigerar problemet där uppdateringen av attributet *[!UICONTROL website scope]* i en viss butiksvy åsidosätter attributvärdena i det globala omfånget.
1. **ACSD-54887**: Korrigerar problemet där kundvagnen raderas efter att kundsessionen har upphört och *[!UICONTROL Persistent Shopping Cart]* är aktiverat.
1. **ACSD-58141**: Korrigerar problemet där `PHPSESSID` återskapar begäranden på POSTEN i butiksområdet för en inloggad kund om [!UICONTROL L2 Redis cache] är aktiverad och kunden uppdateras från Admin.
1. **ACSD-58352**: Korrigerar problemet där returattributetiketter för standardbutiksvyn returneras via GraphQL API när en icke-standardbutiksvy anges i begärandehuvudet.
1. **ACSD-58442**: Korrigerar problemet där enheter med bredden *768px* behandlas som mobila, vilket gör att menyn och huvudet läses in i mobilvyn i stället för i skrivbordsversionen.
1. **ACSD-58790**: Korrigerar funktionen *nypa till zoom* på produktinformationssidans bilder i mobilvyn på [!DNL Chrome].
1. **ACSD-59036**: Korrigerar ett undantag som inträffar när produktpriser läses in med både nedre och övre gränser lika med *$0*.
1. **ACSD-59229**: Korrigerar problemet där kundgruppsrelaterad information sparas i fel segment på grund av det gamla värdet för [!UICONTROL X-Magento-Vary] i begäran.
1. **ACSD-59378**: Korrigerar problemet där URL-skrivningar på butiksnivå uppdateras felaktigt under importen.
1. **ACSD-59514**: Korrigerar problemet där formulär i administrationsområdet med [!DNL Page Builder] återgav *[!DNL Page Builder]i 5 sekunder utan att frigöra lås.* fel i webbläsarkonsolen när formuläret har skickats och ändringarna kan inte sparas.
1. **ACSD-60303**: Korrigerar problemet där en beställning från Admin inte kan placeras om HTML-minification är aktiverat.
1. **ACSD-60441**: Korrigerar problemet med att uppdatera kunder via slutpunkten `V1/customers REST API` när integreringsåtkomsttoken som genererats från serverdelen används.

Använd menyn till vänster för att navigera till en viss korrigeringssida.

