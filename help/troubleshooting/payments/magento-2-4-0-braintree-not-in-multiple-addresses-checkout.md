---
title: 'Adobe Commerce 2.4.0: Braintree inte i kassan för flera adresser'
description: I den här artikeln finns en lösning på ett problem med Adobe Commerce 2.4.0 där betalningsmetoder i Braintree inte ingår i kassan för flera adresser. Observera att problemet har åtgärdats i Adobe Commerce 2.4.1.
exl-id: efde0bba-fd4a-490b-becb-856cb9ea58a5
feature: Checkout, Compliance, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Braintree inte i kassan för flera adresser

I den här artikeln finns en lösning på ett problem med Adobe Commerce 2.4.0 där betalningsmetoder i Braintree inte ingår i kassan för flera adresser. Observera att problemet har åtgärdats i Adobe Commerce 2.4.1.

Obs! Adobe Commerce rekommenderar att du använder tillägget [Commerce Marketplace Braintree](https://marketplace.magento.com/paypal-module-braintree.html) för version 2.3 och senare för att behålla kompatibiliteten med PSD. Tillägget har inte funktioner för utcheckning av flera adresser.

## Berörda produkter och versioner

* Adobe Commerce lokalt v2.4.0
* Adobe Commerce i molninfrastruktur v2.4.0

## Problem

<u>Förutsättningar</u>:

Integreringen med Braintree används.

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

Braintree är inte tillgängligt som betalningsmetod.

## Tillfällig lösning

Aktivera inte alternativ för flera adresser om du använder Braintree i Adobe Commerce 2.4.0. Problemet har åtgärdats i Adobe Commerce 2.4.1.

## Relaterad läsning i vår kunskapsbas

* [Problem med Adobe Commerce 2.4.0 - uppdateringen av kundens aktiviteter fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0: Raw-meddelandedata visas i butiken](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problem med Adobe Commerce 2.4.0 - Export Tax Rates fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0: Knappen &quot;Lägg till markeringar i kundvagnen&quot; fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
