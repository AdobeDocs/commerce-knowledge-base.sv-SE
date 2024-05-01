---
title: GraphQL-fråga för att dölja kategorier fungerar inte med den delade B2B-katalogen
description: Den här artikeln innehåller en lösning för när funktionen för delad B2B-katalog inte fungerar med frågan för GraphQL-kategorier för att dölja kategorier.
exl-id: bdafa8d9-b637-409e-86b5-d132bccfe0b8
feature: B2B, Catalog Management, Categories, GraphQL, Customer Service
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# GraphQL-fråga för att dölja kategorier fungerar inte med den delade B2B-katalogen


## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur och Adobe Commerce lokal 2.4.3

## Problem

GraphQL `categoryList` frågor ignorerar kategoribehörigheten för att dölja kategorier i en delad katalog. Detta händer alla handlare på Adobe Commerce 2.4.3 med funktionen för delad katalog i B2B aktiverad.

<u>Steg som ska återskapas</u>:

Förutsättningar:

Detta händer alla handlare på Adobe Commerce 2.4.3 med PWA storefront-förbrukande GraphQL-API med Adobe Commerce back end/Admin som har funktionen för delad katalog för B2B aktiverad.

1. Skapa flera kategorier (CAT1,CAT2).
1. Skapa en privat delad katalog.
1. Skapa en företagsanvändare och tilldela den till den ovan delade katalogen.
1. Tilldela några produkter till var och en av dessa kategorier.
1. Tilldela CAT1 till den anpassade katalogen och ta bort tilldelningen CAT2 från den anpassade privata katalogen. Detta tar bort tilldelningen av alla produkter från CAT2 från den delade katalogen.
1. Spara den anpassade katalogen.
1. Ange kategoribehörighet för CAT2 till *Neka* Bläddringskategori och ställ in kundgruppen på ovanstående privata katalog.
1. Kör `categoryList query` eller kategorifrågan som företagsanvändare från steg tre.

<u>Förväntade resultat</u>:

Endast CAT1 visas i resultatet.

<u>Faktiska resultat</u>:

Alla kategorier visas oavsett om de har tilldelats/inte tilldelats i den delade katalogen eller vilka kategoribehörigheter som finns.

## Orsak

Funktionaliteten implementerades inte.

## Lösning

Problemet kommer att åtgärdas i version 2.4.4 och handlarna bör [skicka en biljett](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) för att få ett anpassat plåster om de behöver en lösning före version 2.4.4.

## Relaterad läsning

* [Bästa praxis Adobe Commerce antal kategorier begränsningar](https://support.magento.com/hc/en-us/articles/360048176832) i vår kunskapsbas för support.
