---
title: 'Adobe Commerce 2.4.0: Braintree inte i kassan för flera adresser'
description: I den här artikeln beskrivs en tillfällig lösning på ett Adobe Commerce 2.4.0-problem där Braintree betalningsmetoder inte ingår i utcheckningen av flera adresser. Observera att problemet har åtgärdats i Adobe Commerce 2.4.1.
exl-id: efde0bba-fd4a-490b-becb-856cb9ea58a5
feature: Checkout, Compliance, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Braintree inte i kassan för flera adresser

I den här artikeln beskrivs en tillfällig lösning på ett Adobe Commerce 2.4.0-problem där Braintree betalningsmetoder inte ingår i utcheckningen av flera adresser. Observera att problemet har åtgärdats i Adobe Commerce 2.4.1.

Obs! Adobe Commerce rekommenderar att du använder [Commerce Marketplace Braintree-tillägget](https://marketplace.magento.com/paypal-module-braintree.html) för version 2.3 och senare för att behålla PSD-kompatibiliteten. Tillägget har inte funktioner för utcheckning av flera adresser.

## Berörda produkter och versioner

* Adobe Commerce lokalt v2.4.0
* Adobe Commerce i molninfrastruktur v2.4.0

## Problem

<u>Förutsättningar</u>:

Braintree-integreringen används.

<u>Steg som ska återskapas</u>:

1. Gå till butiken.
1. Logga in som kund.
1. Lägg en produkt i kundvagnen.
1. Öppna kundvagnen.
1. Tryck på **Visa och redigera kundvagn**.
1. Tryck på **Checka ut med flera adresser**.
1. Tryck på **Gå till leveransinformation**.
1. Tryck på **Fortsätt till faktureringsinformation**.

<u>Förväntat resultat</u>:

Braintree finns som betalningsmetod.

<u>Faktiskt resultat</u>:

Braintree finns inte som betalningsmetod.

## Tillfällig lösning

Aktivera inte alternativ för flera adresser om du använder Braintree i Adobe Commerce 2.4.0. Problemet har åtgärdats i Adobe Commerce 2.4.1.

## Relaterad läsning i vår kunskapsbas

* [Problem med Adobe Commerce 2.4.0 - uppdateringen av kundens aktiviteter fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problem med Adobe Commerce 2.4.0 - Export Tax Rates fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0: Knappen &quot;Lägg till markeringar i kundvagnen&quot; fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
