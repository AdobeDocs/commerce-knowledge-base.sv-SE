---
title: Exakt matchningssökning fungerar inte i Adobe Commerce 2.4.x
description: Den här artikeln innehåller ett förtydligande av problemet där sökresultat för butiksadresser som använder samma söksträng skiljer sig åt i Adobe Commerce 2.4.x jämfört med Adobe Commerce 2.3.x.
exl-id: 0867558e-1d74-4b83-abf3-651ca7fc32cb
feature: Products, Search
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
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

Du har produkter med attributvärden `Saga 1` och `Saga 16` i både Adobe Commerce 2.3- och Adobe Commerce 2.4-butiker.

<u>Steg som ska återskapas:</u>

1. På framsidan av en Adobe Commerce 2.3-butik anger du *Saga 1* i sökfältet och klicka på **Sök**.
1. Observera att du bara får produkterna med attributvärdet i sökresultaten `Saga 1`.
1. På framsidan av en Adobe Commerce 2.4-butik anger du *Saga 1* i sökfältet och klicka på **Sök**.

<u>Faktiskt resultat:</u>

Sökresultat i 2.4 innehåller produkter med attributvärden `Saga 1` och `Saga 16`.

<u>Förväntat resultat:</u>

Sökresultaten i 2.4 liknar 2.3 och inkluderar endast produkter med attributvärde `Saga 1`.

## Orsak

Adobe Commerce inbyggda sökfunktion som används i 2.3.x ger exakt matchande sökresultat. Medan Live Search är en valfri modul som är tillgänglig för installation och som släpptes med Adobe Commerce 2.4.x, implementeras på ett annat sätt, och det faktiska resultatet är det förväntade beteendet när modulen används.

## Relaterad läsning

[Installera Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) i vår användarhandbok.

[Live Search](https://devdocs.magento.com/live-search/overview.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=Live%20Search) i vår dokumentation för utvecklare.
