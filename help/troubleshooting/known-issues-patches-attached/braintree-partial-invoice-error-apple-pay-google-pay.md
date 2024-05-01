---
title: "Adobe Commerce 2.4.4: Det går inte att skapa partiella fakturor"
description: I den här artikeln finns en snabbkorrigering för problemet där användare inte kan skapa partiella fakturor när de använder Apple Pay eller Google Pay via Braintree som betalningsmetoder.
exl-id: bf78cc07-9dc7-4eb8-bfdf-57ea5131effb
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Adobe Commerce 2.4.4: Det går inte att skapa partiella fakturor

I den här artikeln finns en snabbkorrigering för problemet där användare inte kan skapa partiella fakturor när de använder Apple Pay eller Google Pay via Braintree som betalningsmetoder.

## Berörda produkter och versioner

Adobe Commerce (alla distributionsmetoder) 2.4.4

## Problem

När man använder Apple Pay eller Google Pay som betalningsmetod får man felmeddelandet &quot;*Kommandot vault_capture finns inte. Kontrollera kommandot och försök igen.*&quot; när partiella fakturor skapades.

<u>Steg som ska återskapas</u>:

1. Öppna Adobe Commerce webbplats.
1. Lägg en enkel produkt i kundvagnen (kvantitet 2).
1. Välj **Apple Pay** eller **Google Pay** som betalningsmetod från kundvagnen.
1. Beställ.
1. Öppna orderinformation från back end.
1. Skapa en delfaktura.
1. Skapa en annan faktura för det återstående beloppet.

<u>Förväntade resultat</u>:

Partiella fakturor skapas.

<u>Faktiska resultat</u>:

Den första partiella fakturan skapas. När användaren skapar den andra delfakturan visas följande fel: *Kommandot vault_capture finns inte. Verifiera kommandot och försök igen*.

## Orsak

Adobe Commerce sparar kreditkortsinformation i valvet för att skapa partiella fakturor. För närvarande finns det ingen funktionalitet att välja mellan Apple Pay och Google Pay.

## Lösning

Åtgärda problemet genom att installera följande patch:

[Braintree_disabled_partiell_capture_for_appleplay_googleplay.zip](assets/braintree-disabled-partial-capture-for-applepay-googlepay.zip)

## Så här använder du patchen

Se [Använda en kompositkorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) för instruktioner.
