---
title: 'Adobe Commerce 2.4.2: Betalningen till Braintree Venmo fungerar inte'
description: I den här artikeln beskrivs ett känt Adobe Commerce 2.4.2-problem där beställningar inte genereras när du använder Braintree Venmo vid utcheckning. Det finns för närvarande ingen upplösning.
exl-id: 1832ab64-5024-444b-915e-473b34979a6e
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Adobe Commerce 2.4.2: Betalningen till Braintree Venmo fungerar inte

I den här artikeln beskrivs ett känt Adobe Commerce 2.4.2-problem där beställningar inte genereras när du använder Braintree Venmo vid utcheckning. Det finns för närvarande ingen upplösning.

## Berörda produkter och versioner

* Adobe Commerce (alla distributionsmetoder) 2.4.2

## Problem

<u>Förhandsvillkor</u> :

Aktivera Venmo-betalning i konfigurationen Braintree.

<u>Steg som ska återskapas</u> :

1. I butiken lägger du till en artikel i kundvagnen.
1. Gå till **Utcheckning**.
1. Välj leveranssätt.
1. Välj **Venmo** som betalningsmetod.
1. Klicka på **Betala med Venmo**.
1. Klicka på **Montera order**.

<u>Faktiska resultat</u>:

Ordern skapas inte i Adobe Commerce-koden när kunden har omdirigerats tillbaka till butiken från appen Venmo, och inget felmeddelande visas. Ordern skapas i Braintree.

<u>Förväntade resultat</u>:

Ordern skapas i Adobe Commerce när kunden har omdirigerats tillbaka till butiken från appen Venmo och ordern skapas i Braintree, som förväntat.

## Lösning

Det finns för närvarande ingen upplösning.
