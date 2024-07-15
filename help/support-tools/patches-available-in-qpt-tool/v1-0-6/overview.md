---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.0.6'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.0.6.
exl-id: 38e9454b-e278-4b14-a861-2af0623db92e
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.6 - översikt

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i [!DNL Quality Patches Tool] (QPT) v1.0.6.

QPT v1.0.6 innehåller följande patchar:

1. **MDVA-28202**: Korrigerar problemet där lagernavigering inte filtrerar konfigurerbara produkter korrekt när MSI används.
1. **MDVA-28300**: Korrigerar problemet där GQL-begäran inte återspeglar prisändringar från katalogprisregler.
1. **MDVA-28993**: Implementerar funktionen *Minimum ska matcha* och partiell sökning för motorn [!DNL Elasticsearch]. Löser problem med bindestreck i sökfrågor.
1. **MDVA-29446**: Korrigerar problemet där priset för ej tillämplig leveransmetod visas som noll vid utcheckning.
1. **MDVA-29787**: Korrigerar problemet där målregeln för relaterade produkter inte fungerar när *är ett av* -villkoren används för att definiera produkter som ska visas.
1. **MDVA-30102**: Korrigerar problemet där [!DNL Redis]-cachen växer snabbt eftersom layoutcachen inte har TTL.
1. **MDVA-30357**: Korrigerar problemet med fel bild-URL:er som skapas när en platskarta genereras av cron.
1. **MDVA-30565**: Korrigerar problemet där *Ingen sådan entitet med cartid = 0*-fel visas för gästkunden i kassan i butiken om beständig kundvagn är aktiverad.
1. **MDVA-30599**: Korrigerar problemet där gästcitat som skapats med API felaktigt markeras som offerter för inloggade kunder.
1. **MDVA-30977**: Korrigerar problemet med att slumpmässiga produkter saknas i kategorier efter omindexering.
1. **MDVA-31006**: Korrigerar problemet där duplicerade order visas efter att en order har lagts med betalningen [!DNL Paypal Express].

Använd menyn till vänster för att navigera till en viss korrigeringssida.
