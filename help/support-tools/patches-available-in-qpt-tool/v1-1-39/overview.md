---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.39'
description: Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av patcharna i [!DNL Quality Patches Tool] (QPT) v1.1.39.
feature: Tools and External Services
role: Admin, Developer
exl-id: 48563701-0fa0-4c88-943e-78b421b806b5
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Översikt [!DNL Quality Patches Tool] (QPT) v1.1.39

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av patcharna i [!DNL Quality Patches Tool] (QPT) v1.1.39.

QPT v1.1.39 innehåller följande patchar:

1. **ACSD-53704**: Korrigerar problemet där historiken för belöningspoängsaldo felberäknas efter att belöningspoäng har gått ut.
1. **ACSD-53583**: Förbättrar prestanda för partiell omindexering för *Kategoriprodukter* och *Produktkategorier* indexerare.
1. **ACSD-54026**: Korrigerar ett felaktigt felmeddelande för ett `updateCompanyRole` GraphQL begär en obehörig användare.
1. **ACSD-54106**: Korrigerar problemet där produktsortering efter namn för turkiska accenttecken är felaktig.
1. **ACSD-52219**: Korrigerar problemet där administratörsrutnät inte fungerar som väntat när du växlar mellan olika bokmärkesvyer ofta.
1. **ACSD-54342**: Korrigerar ett felaktigt felmeddelande *Fel i datastruktur: värdena är blandade* när en CSV-fil importeras utan giltiga data.
1. **ACSD-54660**: Ett nytt indataattribut har lagts till *sortera* för att sortera kundorder i GraphQL efter `sort_field` och `sort_direction`.
1. **ACSD-54776**: Åtgärdar problemet där det inte är markerat *[!UICONTROL Use Default Value]* och värden som inte är standardvärden för produktfält sparas inte för den andra webbplatsen, butiken och butiksvyn.
1. **ACSD-53998**: Åtgärdar problemet där **[!UICONTROL Dynamic Block]** baserat på en **[!UICONTROL Customer Segment]** fungerar inte korrekt efter utloggning från ett kundkonto.
1. **ACSD-53204**: Korrigeringar *Det går inte att spara produkten.* fel vid samtidig begäran om att lägga till bilder i produktgalleriet med `rest/V1/products/<sku>/media` slutpunkt.
1. **ACSD-47657**: En cachelagringsmekanism för AWS inloggningsuppgifter har lagts till. En autentiseringsprovider använder nu cacheminnet i Magento för att cachelagra autentiseringsuppgifter som hämtats från AWS för EC2-konfiguration.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
