---
title: '"Adobe Commerce 2.4.0 known issue: missing "Refund" label in Klarna'
description: I den här artikeln finns en lösning på ett känt problem i Admin för ett saknat **Refund**-märke i Klarna VBE (Vendor Bundled Extension). När det är i Klarna-portalen som gör en återbetalning visas inte etiketten **Refund** bredvid den paketerade produkten som har återbetalats.
exl-id: f08039b2-7f8b-481e-8ec8-1659e227744f
feature: B2B, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 Känt fel: etiketten&quot;Refund&quot; saknas i Klarna

I den här artikeln beskrivs en tillfällig lösning för ett känt fel i Admin för etiketten **Återbetalning** som saknas i Klarna VBE (leverantörspaketerat tillägg). När det är i Klarna-portalen som utför en återbetalning visas inte etiketten **Återbetalning** bredvid den paketerade produkt som har återbetalats.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.4.0
* Adobe Commerce om molninfrastruktur 2.4.0

## Problem

<u>Förutsättningar:</u>

* Klarna är aktiverade.
* En paketerad produkt skapas.

<u>Steg som ska återskapas</u>

1. Gå till Adobe Commerce klientdel och lägg till en paketerad produkt i **kundvagnen**.
1. Navigera till kassan.
1. Ange konsumentinformation i kassan och klicka på **Nästa**.
1. Välj **KP-alternativ** och klicka på **Montera ordning**.
1. Gå till **Admin** > **Försäljning** > **Beställningar**.
1. Öppna ordern.
1. Skapa faktura för produkt.
1. Gå till **Fakturor** > **Välj faktura** > Klicka på **Kreditnota** > Klicka på **Återbetalning** (inte **Återbetalning offline**).
1. Gå till Klarna portal.
1. Öppna ordern.
1. Etiketten **Återbetalning** finns.

<u>Förväntat resultat</u>

På Klarna-portalen visas etiketten **Återbetalning** bredvid den produkt som återbetalades.

<u>Faktiskt resultat</u>

På Klarna-portalen visas inte etiketten **Återbetalning** bredvid den produkt som återbetalades.

## Tillfällig lösning

Du kan lösa problemet genom att ignorera etiketten **Återbetalning** som saknas i Klarna-portalen för återfinansierade paketerade produkter. Återbetalningen har gjorts, även om etiketten **Återbetalning** inte visades. Problemet förväntas bli åtgärdat i Adobe Commerce 2.4.1, som kommer att släppas tredje kvartalet 2020.

## Relaterade läsningar i vår kunskapsbas:

* [Adobe Commerce 2.4.0: Raw-meddelandedata visas i butiken](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0: Exportavgifter fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0: Braintree betalningsmetoder visas inte i kassan för flera adresser](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problem med Adobe Commerce 2.4.0: Felmeddelande vid val av lokal betalningsmetod för vissa länder vid utcheckning](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0 Känt fel: 404-fel vid borttagning av poäng vid utcheckning av flera leveranser](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Adobe Commerce 2.4.0: fel vid visning av beställningar](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B Admin kan inte lägga till en konfigurerbar produkt att citera](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problem med att skapa etiketter i Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Problem med Adobe Commerce 2.4.0 - uppdateringen av kundens aktiviteter fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0: Knappen &quot;Lägg till markeringar i kundvagnen&quot; fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
