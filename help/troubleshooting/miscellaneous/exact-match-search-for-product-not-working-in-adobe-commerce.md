---
title: Exakt matchningssökning fungerar inte i Adobe Commerce 2.4.x
description: Den här artikeln innehåller ett förtydligande av problemet där sökresultat för butiksadresser som använder samma söksträng skiljer sig åt i Adobe Commerce 2.4.x jämfört med Adobe Commerce 2.3.x.
exl-id: 0867558e-1d74-4b83-abf3-651ca7fc32cb
feature: Products, Search
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Exakt matchningssökning fungerar inte i Adobe Commerce 2.4.x

Den här artikeln innehåller ett förtydligande av problemet där sökresultat för butiksadresser som använder samma söksträng skiljer sig åt i Adobe Commerce 2.4.x jämfört med Adobe Commerce 2.3.x.

## Berörda produkter och versioner

- Adobe Commerce (alla distributionsmetoder) 2.4.x, 2.3.x
- Live Search

## Problem

<u>Förutsättningar:</u>

Du har produkter med attributvärdena `Saga 1` och `Saga 16` i både Adobe Commerce 2.3- och Adobe Commerce 2.4-butiker.

<u>Steg att återskapa:</u>

1. Ange *Saga 1* i sökfältet i butiken framför en Adobe Commerce 2.3-butik och klicka på **Sök**.
1. Observera att du bara får produkter med attributvärdet `Saga 1` i sökresultaten.
1. Ange *Saga 1* i sökfältet i butiken framför en Adobe Commerce 2.4-butik och klicka på **Sök**.

<u>Faktiskt resultat:</u>

Sökresultat i 2.4 innehåller produkter med attributvärdena `Saga 1` och `Saga 16`.

<u>Förväntat resultat:</u>

Sökresultaten i 2.4 liknar 2.3 och inkluderar endast produkter med attributvärdet `Saga 1`.

## Orsak

Adobe Commerce inbyggda sökfunktion som används i 2.3.x ger exakt matchande sökresultat. Medan Live Search är en valfri modul som är tillgänglig för installation och som släpptes med Adobe Commerce 2.4.x, implementeras på ett annat sätt, och det faktiska resultatet är det förväntade beteendet när modulen används.

## Relaterad läsning

[Installera Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=sv-SE) i vår användarhandbok.

[Livesökning](https://experienceleague.adobe.com/sv/docs/commerce-merchant-services/live-search/overview) i utvecklardokumentationen.
