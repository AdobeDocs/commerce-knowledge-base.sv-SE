---
title: "Adobe Commerce 2.4.0, 2.4.1: Aktivera partiell faktura för Braintree Venmo"
description: I den här artikeln beskrivs en känd utgåva av Adobe Commerce 2.4.0 och 2.4.1, där det inte finns någon partiell faktura för beställningar som gjorts med Braintree via Venmo.
exl-id: ef6c8aa4-a2a7-4e07-a957-23173017baf2
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Adobe Commerce 2.4.0, 2.4.1: Aktivera partiell faktura för Braintree Venmo

I den här artikeln beskrivs en känd utgåva av Adobe Commerce 2.4.0 och 2.4.1, där det inte finns någon partiell faktura för beställningar som gjorts med Braintree via Venmo.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.4.0 och 2.4.1
* Adobe Commerce i molninfrastruktur 2.4.0 och 2.4.1

## Problem

<u>Förutsättningar:</u>

I konfigurationen för betalningsmetoden Braintree anger du **Aktivera Venmo via Braintree** = *Ja* med **Betalningsåtgärd** = *Auktorisering*; **Aktivera valv för kortbetalningar** = *Nej*.

<u>Steg att återskapa:</u>

1. Skapa en beställning för två eller flera produkter med Venmo (Braintree) som betalningsmetod.
1. Öppna beställningen i Commerce Admin.
1. Skapa en faktura för en av de beställda produkterna.
1. Försök att skapa faktura för resten av beställda produkter.

<u>Förväntat resultat:</u>

Fakturan har skapats.

<u>Faktiskt resultat:</u>

Följande felmeddelande visas: *Kommandot &quot;vault\_capture&quot; finns inte. Verifiera kommandot och försök igen.*

## Tillfällig lösning

Fånga hela beloppet när du skapar fakturor för beställningar som gjorts med Braintree via Venmo.
