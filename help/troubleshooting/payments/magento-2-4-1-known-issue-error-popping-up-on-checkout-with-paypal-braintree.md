---
title: "Adobe Commerce 2.4.1 Känt fel: fel uppstår vid utcheckning med PayPal Braintree"
description: I den här artikeln beskrivs ett känt Adobe Commerce 2.4.1-problem, där ett felmeddelande visas och försvinner i faktureringssteget i utcheckningen om betalning från PayPal Braintree används och flera adresser skickas.
exl-id: db3830b2-4885-4d89-85cd-bdcbd4b396e6
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 Känt fel: fel vid utcheckning med PayPal Braintree

I den här artikeln beskrivs ett känt Adobe Commerce 2.4.1-problem, där ett felmeddelande visas och försvinner i faktureringssteget i utcheckningen om betalning från PayPal Braintree används och flera adresser skickas.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur 2.4.1
* Adobe Commerce lokal 2.4.1

## Problem

Ett felmeddelande visas och försvinner i faktureringssteget i Checka ut om betalning från PayPal Braintree används och flera adresser skickas markerade.

<u>Steg som ska återskapas:</u>

1. Logga in som kund i butiken (kan vara en gästutcheckning om den är aktiverad i Admin).
1. Lägg en produkt i kundvagnen.
1. Klicka för att öppna kundvagnsförhandsvisningen.
1. Klicka **Visa och redigera kundvagn**.
1. Klicka på **Checka ut med flera adresser**.
1. Klicka **Gå till leveransinformation** och ange adresserna.
1. Klicka **Fortsätt till faktureringsinformation**.
1. Välj **PayPal Braintree** och klicka på **PayPal** -knappen.
1. I popup-fönstret klickar du på **Godkänn och betala**.

<u>Förväntat resultat:</u>

Ordern placeras utan fel.

<u>Faktiskt resultat:</u>

Ordern placeras, men med ett fel. The *Det gick inte att initiera PayPal-utcheckning. Kontakta butiksägaren*.  -fel visas en sekund och försvinner.

## Korrigera

Eftersom orderplaceringen inte är blockerad behöver du inte utföra några åtgärder.
