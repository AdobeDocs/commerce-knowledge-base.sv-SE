---
title: 'Adobe Commerce 2.4.0: Knapparna Skapa ny order saknas'
description: I den här artikeln finns en lösning på ett känt problem i Commerce Admin för två saknade knappar på sidan för att skapa order. När du skapar en ny beställning för en ny eller befintlig kund går det inte att lägga till produkter i beställningen från katalogen eftersom knapparna **Lägg till produkter efter SKU** och **Lägg till produkter** saknas. Detta orsakas av att JS-paketering har aktiverats. En fix kommer att finnas i Adobe Commerce 2.4.1.
exl-id: 24ae880e-6d74-4444-9165-2744b12af81a
feature: B2B
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Knapparna Skapa ny order saknas

I den här artikeln finns en lösning på ett känt problem i Commerce Admin för två saknade knappar på sidan för att skapa order. När du skapar en ny beställning för en ny eller befintlig kund går det inte att lägga till produkter i beställningen från katalogen eftersom knapparna **Lägg till produkter efter SKU** och **Lägg till produkter** saknas. Detta orsakas av att JS-paketering har aktiverats. En fix kommer att finnas i Adobe Commerce 2.4.1.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.4.0
* Adobe Commerce om molninfrastruktur 2.4.0

## Problem

<u>Steg som ska återskapas</u>

1. Gå till **Kunder > Alla kunder**.
1. Klicka på länken **Redigera** för en kund.
1. Klicka på knappen **Skapa ordning** .

<u>Förväntat resultat</u>

Knapparna **Lägg till produkter efter SKU** och **Lägg till produkter** visas på sidan **Skapa ny ordning**.

<u>Faktiskt resultat</u>

Knapparna **Lägg till produkter efter SKU** och **Lägg till produkter** saknas på sidan **Skapa ny ordning**.

## Tillfällig lösning

Problemet åtgärdas genom att JS-paketering inaktiveras för Adobe Commerce-instansen. Problemet förväntas bli åtgärdat i Adobe Commerce 2.4.1, som kommer att släppas tredje kvartalet 2020.

## Relaterade läsningar i vår kunskapsbas

* [Adobe Commerce 2.4.0: Exportavgifter fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0: Braintree betalningsmetoder visas inte i kassan för flera adresser](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problem med Adobe Commerce 2.4.0: Felmeddelande vid val av lokal betalningsmetod för vissa länder vid utcheckning](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0 B2B Admin kan inte lägga till en konfigurerbar produkt att citera](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problem med Adobe Commerce 2.4.0 - uppdateringen av kundens aktiviteter fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0: Knappen &quot;Lägg till markeringar i kundvagnen&quot; fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
