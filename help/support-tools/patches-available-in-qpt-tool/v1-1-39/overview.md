---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.39'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.39.
feature: Tools and External Services
role: Admin, Developer
exl-id: 48563701-0fa0-4c88-943e-78b421b806b5
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.39

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i [!DNL Quality Patches Tool] (QPT) v1.1.39.

QPT v1.1.39 innehåller följande patchar:

1. **ACSD-53704**: Korrigerar problemet där historiken för belöningspoängsaldo inte beräknas efter att belöningspoäng har förfallit.
1. **ACSD-53583**: Förbättrar prestanda för partiell omindexering för *Kategoriprodukter* och *produktkategorier*.
1. **ACSD-54026**: Korrigerar ett felaktigt felmeddelande för en `updateCompanyRole` GraphQL-begäran för en obehörig användare.
1. **ACSD-54106**: Korrigerar problemet där produktsortering efter namn för turkiska accenttecken är felaktig.
1. **ACSD-52219**: Korrigerar problemet där administratörsrutnät inte fungerar som förväntat när du ofta växlar mellan olika bokmärkesvyer.
1. **ACSD-54342**: Korrigerar ett felaktigt felmeddelande *Fel i datastrukturen: värdena blandas* vid import av en CSV-fil utan giltiga data.
1. **ACSD-54660**: Ett nytt indataattribut, *sort*, lades till för att sortera kundorder i GraphQL efter `sort_field` och `sort_direction`.
1. **ACSD-54776**: Korrigerar problemet där avmarkerade *[!UICONTROL Use Default Value]* och icke-standardvärden för produktfält inte sparas för den andra webbplatsen, butiken och butiksvyn.
1. **ACSD-53998**: Korrigerar problemet där en **[!UICONTROL Dynamic Block]** baserad på en **[!UICONTROL Customer Segment]** inte fungerar korrekt efter utloggning från ett kundkonto.
1. **ACSD-53204**: Korrigeringar *Produkten kan inte sparas.*-fel vid samtidig begäran om att lägga till bilder i produktgalleriet med slutpunkten `rest/V1/products/<sku>/media`.
1. **ACSD-47657**: En cachelagringsmekanism för AWS-autentiseringsuppgifter har lagts till. En autentiseringsprovider använder nu cacheminnet i Magento för att cachelagra autentiseringsuppgifter som hämtats från AWS för EC2-konfiguration.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
