---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.42'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.42.
feature: Tools and External Services
role: Admin, Developer
exl-id: 49f7ebd6-7a5f-49da-8fac-c3c2b73b52c1
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.42

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i [!DNL Quality Patches Tool] (QPT) v1.1.42.

QPT v1.1.42 innehåller följande patchar:

1. **ACSD-53658**: Korrigerar problemet där *[!UICONTROL Recently Viewed]* produktdata inte uppdateras korrekt i butiksvyn.
1. **ACSD-54626**: Korrigerar problemet där du inte kan skapa en ny inköpsorderregel (`createPurchaseOrderApprovalRule`) med attributet `NUMBER_OF_SKUS` via GraphQL.
1. **ACSD-53845**: Korrigerar tidsgränsen för MySQL-anslutningen när `consumer max_messages` = 0.
1. **ACSD-54890**: Korrigerar problemet där `aggregate_sales_report_bestsellers_data` orsakar MySQL-fel på grund av att diskutrymmet på `/tmp` är slut.
1. **ACSD-55112**: Korrigerar problemet där knappen *[!UICONTROL Submit review]* kan klickas flera gånger utan [!DNL Google reCAPTCHA v3]-validering.
1. **ACSD-54264**: Korrigerar problemet där felmeddelandet *Du kan inte uppdatera det begärda attributet. Rad-ID: store_id* visas när en kund försöker checka ut med en överlåtbar offert från en annan butiksvy.
1. **ACSD-54418**: Korrigerar problemet där ett fast rabattbelopp felaktigt tillämpas på varje underordnad produkt i det dynamiskt prissatta paketet.
1. **ACSD-55238**: Korrigerar problemet med att den tomma produktmetabeskrivningen sparades.
1. **ACSD-54966**: Korrigerar problemet där en kupongkod med begränsad användning per kund inte kan återanvändas om föregående order misslyckas.
1. **ACSD-54060**: Korrigerar problemet där en begränsad administratör inte kan spara en produkt om den är underordnad en annan produkt som tilldelats ett annat omfång.
1. **ACSD-48910**: Korrigerar problemet där en paketerad produkt som tilldelats flera källor går ut ur lagret efter att en order har fakturerats och skickats, även om den har en kvantitet som inte är noll.
1. **ACSD-55381**: Korrigerar ett internt serverfel vid sökning efter `configurable_product_option_uid`- och `configurable_product_option_value_uid`-fält från ett B2B *[!UICONTROL Requisition list]* via GraphQL.
1. **ACSD-55628**: Korrigerar överföring av en fil i företagsregistreringsformuläret och ersättning av en fil för ett kundattribut i butiken.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
