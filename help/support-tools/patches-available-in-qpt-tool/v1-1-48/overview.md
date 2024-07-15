---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.48'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.48.
feature: Tools and External Services
role: Admin, Developer
exl-id: 6170c616-312c-4de3-98dc-e2c27c376608
source-git-commit: 42712af2ce4337cd64b8dea555139e4252fb91cf
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.48

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i [!DNL Quality Patches Tool] (QPT) v1.1.48.

QPT v1.1.48 innehåller följande patchar:

1. **ACSD-55566**: Korrigerar problemet där *[!UICONTROL mergeCart mutation]* misslyckas med ett *internt serverfel* i GraphQL-svar när käll- och destinationskort sammanfogas med samma paketerade objekt.
1. **ACSD-56546**: Korrigerar problemet där konfigurerbara och paketerade produkter visas som *[!UICONTROL Out of Stock]* i butiken när *[!UICONTROL Display Out of Stock Product]*-konfigurationen är inaktiverad.
1. **ACSD-56635**: Korrigerar problemet där den importerade kunden dupliceras med samma e-postadress när importen används med [!UICONTROL Account Sharing] inställd på *[!UICONTROL Global]*.
1. **ACSD-56741**: Korrigerar felmeddelandet *Försöker få åtkomst till matrisförskjutning på värdet av typen null* som visas under `setup:upgrade` när databasen innehåller en anpassad MySQL-utlösare som inte är relaterad till indexeringsmekanismen och [!DNL MView].
1. **ACSD-57315**: Korrigerar problemet där en ny transaktion skapas i [!DNL PayPal Payflow Pro] varje gång knappen **[!UICONTROL Fetch]** klickas på skärmen Visa transaktion i [!UICONTROL Admin].
1. **ACSD-57337**: Korrigerar problemet där en administratörsanvändare med åtkomstbegränsningar för specifika webbplatser kan se företag från alla webbplatser i rutnätet *[!UICONTROL Companies]*.
1. **ACSD-57394**: Korrigerar felaktig produktsortering efter flera sorteringsfält i GraphQL.
1. **ACSD-57565**: Korrigerar problemet där kontrollpanelen *[!UICONTROL Order]* visar felaktig ordningsinformation tills tidsperioden har uppdaterats. På kontrollpanelen visas nu korrekt orderstatistik vid första inläsningen.
1. **ACSD-57854**: Korrigerar problemet där produkt-GraphQL begär returnerar inaktiverade kategorier i kategoriaggregeringarna.
1. **ACSD-58008**: Korrigerar problemet där en schemalagd uppdatering tar bort den tidigare versionen av det mellanlagrade objektet om inget slutdatum anges.

Använd menyn till vänster för att navigera till en viss korrigeringssida.

