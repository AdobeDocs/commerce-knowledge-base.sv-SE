---
title: 'Adobe Commerce 2.4.0: Utcheckningsfel vid val av lokala betalningar'
description: Den här artikeln handlar om en lösning på ett känt problem i Adobe Commerce vid utcheckning där ett felmeddelande visas när du väljer en lokal betalningsmetod för vissa länder. Detta gäller länderna Belgien, Italien, Nederländerna, Polen och Spanien.
exl-id: de2eafb0-d03c-4ff8-9615-0f2676d95848
feature: B2B, Categories, Checkout, Orders, Payments
role: Developer
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Utcheckningsfel vid val av lokala betalningar

Den här artikeln handlar om en lösning på ett känt problem i Adobe Commerce vid utcheckning där ett felmeddelande visas när du väljer en lokal betalningsmetod för vissa länder. Detta gäller länderna Belgien, Italien, Nederländerna, Polen och Spanien.

Felmeddelandet *Det finns för närvarande inga tillgängliga betalningsmetoder. Uppdatera din faktureringsadress.* kommer att visas, men de lokala betalningsmetoderna kommer fortfarande att visas och fungera korrekt. En permanent programfix finns i Adobe Commerce 2.4.1.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.4.0
* Adobe Commerce om molninfrastruktur 2.4.0

## Problem

<u>Förutsättningar</u>:

* Adobe Commerce 2.4.0 är installerat.
* Skapa en produkt och en kategori.
* Konfigurera betalningsmetoden [Braintree](https://developer.adobe.com/commerce/webapi/graphql/payment-methods/braintree/).

<u>Steg som ska återskapas</u>:

1. Navigera till butiken.
1. Välj artiklar att lägga till i kundvagnen.
1. Gå till kassan.
1. Fyll i adressformuläret med en giltig adress.
1. Gå till sidan för granskning och betalningar.

<u>Förväntat resultat</u>:

De lokala betalningsmetoderna ska visas som vanligt, utan något felmeddelande.

<u>Faktiskt resultat</u>:

Felmeddelandet *Det finns för närvarande inga tillgängliga betalningsmetoder. Uppdatera din faktureringsadress.* visas, men de lokala betalningsmetoderna visas och fungerar fortfarande korrekt.

## Lösning

Lösningen är att ignorera det visade felmeddelandet och fortsätta med betalningen som vanligt, eftersom alla lokala betalningsmetoder fungerar normalt. Korrigeringen var tillgänglig från och med Adobe Commerce version 2.4.1.

## Relaterad läsning

* [Adobe Commerce 2.4.0: Raw-meddelandedata visas i butiken](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0: Exportavgifter fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0: Braintree betalningsmetoder visas inte i kassan för flera adresser](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problem med Adobe Commerce 2.4.0: Uppdatering av kundens aktiviteter fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B Admin kan inte lägga till en konfigurerbar produkt att citera](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
