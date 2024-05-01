---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.0.8'
description: Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av patcharna i [!DNL Quality Patches Tool] (QPT) v1.0.8.
exl-id: 6cd3eabe-067f-4e80-b17f-561290499261
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.8 - översikt

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av patcharna i [!DNL Quality Patches Tool] (QPT) v1.0.8.

QPT v1.0.8 innehåller följande patchar:

1. **MDVA-28357**: Ersätter standardanalyseraren med en anpassad analyserare med nyckelordstoken för SKU-fältet i [!DNL ElasticSearch] index för att få sökfrågor med jokertecken att fungera med SKU:er som innehåller ett bindestreck (&quot;-&quot;).
1. **MDVA-29954**: Åtgärdar problemet där *Ny registreringsbegäran för företag* och *Du har länkats till ett företag* e-postmeddelanden skickas från fel adress.
1. **MDVA-30112**: Korrigerar problemet där antalet order överstiger *teckenstorlek* värde, Adobe Commerce ser beställningarna med *väntande* status som inkonsekvenser.
1. **MDVA-30963**: Korrigerar problemet där produktfiltreringsresultat bara innehåller värden som angetts för *Alla butiksvyer* i Admin, ta med produkter med värden som åsidosatts på butiksvynivån.
1. **MDVA-31150**: Korrigerar problemet där butikskreditsaldon och presentkortsaldon inte returneras av API-anropet för GET Invoice Rest, när fakturan bokfördes av Rest API-anrop och ordern delvis betalades av butikskreditkonton och presentkortskonton.
1. **MDVA-31242**: Korrigerar problemet där fel valutasymbol visas i [!UICONTROL Credit Memo] rutnät.
1. **MDVA-31295**: Korrigerar problemet där belöningspoäng inte beräknas när en delorder har slutförts och artiklarna beskattas.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
