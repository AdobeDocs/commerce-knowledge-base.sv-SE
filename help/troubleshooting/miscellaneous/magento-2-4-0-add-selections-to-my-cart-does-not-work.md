---
title: '"Adobe Commerce 2.4.0: "Det går inte att lägga till val i vagnen"'
description: I den här artikeln beskrivs en tillfällig lösning på ett problem med en trasig knapp som är känd i Commerce Admin när du hanterar kundens kundvagn. När du försöker lägga till valda produkter i kundens kundvagn fungerar inte knappen **Lägg till val i min kundvagn** som finns längst ned i avsnittet. Problemet inträffar på alla sidor på administrationspanelen som innehåller två **Lägg till markeringar i kundvagnen**. En permanent programfix finns i Adobe Commerce 2.4.1.
exl-id: b0830ec2-2aea-4afb-8d02-e9c8f54283be
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: &quot;Lägg till markeringar i kundvagnen&quot; fungerar inte

I den här artikeln beskrivs en tillfällig lösning på ett problem med en trasig knapp som är känd i Commerce Admin när du hanterar kundens kundvagn. När du försöker lägga till valda produkter i kundens kundvagn fungerar inte knappen **Lägg till val i kundvagnen** som finns längst ned i avsnittet. Problemet inträffar på alla sidor på Admin-panelen som innehåller två **Lägg till markeringar i kundvagnen** . En permanent programfix finns i Adobe Commerce 2.4.1.

## Berörda produkter och versioner

* Adobe Commerce 2.4.0 (alla distributionsmetoder)

## Problem

<u>Steg som ska återskapas</u>

1. Navigera till en sida på Admin-panelen som innehåller två **Lägg till markeringar i kundvagnen** .
1. Välj artiklar som ska läggas till i kundvagnen.
1. Klicka på knappen **Lägg till markeringar i kundvagnen** som finns längst ned i avsnittet.

<u>Förväntat resultat</u>

Alla markeringar läggs till i vagnen som förväntat.

<u>Faktiskt resultat</u>

Adobe Commerce lägger inte till dina val i kundvagnen.

## Lösning

Knappen **Lägg till markeringar i kundvagnen** som finns högst upp på sidan fungerar fortfarande. Problemet förväntas bli åtgärdat i Adobe Commerce version 2.4.1, som är planerad att släppas under tredje kvartalet 1.

## Relaterad läsning

* [MerchDocs&#39; Managing a Shopping Cart](https://experienceleague.adobe.com/sv/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage) i vår användarhandbok.
* [Adobe Commerce 2.4.0-problem: Raw-meddelandedata visas på butiken](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md) i vår kunskapsbas för support.
* [Problem med Adobe Commerce 2.4.0: Exportskattesatser fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md) i vår kunskapsbas för support.
* [Ett känt fel uppstod i Adobe Commerce 2.4.0: Betalningsmetoder i Braintree visas inte i kassan för flera adresser](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md) i vår kunskapsbas för support.
