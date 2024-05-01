---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.0.6'
description: Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av patcharna i [!DNL Quality Patches Tool] (QPT) v1.0.6.
exl-id: 38e9454b-e278-4b14-a861-2af0623db92e
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.6 - översikt

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av patcharna i [!DNL Quality Patches Tool] (QPT) v1.0.6.

QPT v1.0.6 innehåller följande patchar:

1. **MDVA-28202**: Korrigerar problemet där navigering i lager inte filtrerar konfigurerbara produkter korrekt när MSI används.
1. **MDVA-28300**: Korrigerar problemet där GQL-begäran inte återspeglar prisändringar från katalogprisregler.
1. **MDVA-28993**: Implementerar *Minimivärdet måste matcha* funktionalitet och partiell sökning efter [!DNL Elasticsearch] motor. Löser problem med bindestreck i sökfrågor.
1. **MDVA-29446**: Korrigerar problemet där priset på en leveransmetod som inte är tillämplig visas som noll vid utcheckning.
1. **MDVA-29787**: Åtgärdar ett problem där målregeln för relaterade produkter inte fungerar när *är en av* villkor används för att definiera produkter som ska visas.
1. **MDVA-30102**: Åtgärdar problemet där [!DNL Redis] cacheminnet växer snabbt eftersom layoutcacheminnen inte har TTL.
1. **MDVA-30357**: Åtgärdar problemet med fel bild-URL:er som skapas när en platskarta skapas av cron.
1. **MDVA-30565**: Åtgärdar problemet där *Ingen sådan entitet med cartid = 0* fel visas för gästkund vid utcheckning i butiken om beständig kundvagn är aktiverad.
1. **MDVA-30599**: Korrigerar problemet där gästcitat som skapats med API felaktigt markeras som citattecken för inloggade kunder.
1. **MDVA-30977**: Åtgärdar problemet med slumpmässiga produkter som saknas i kategorier efter omindexering.
1. **MDVA-31006**: Korrigerar problemet där dubblettorder visas efter att en order har lagts med [!DNL Paypal Express] betalning.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
