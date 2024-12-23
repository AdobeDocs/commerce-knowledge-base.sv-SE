---
title: 'Vertex Address Cleansing: olika adresser tillåts inte'
description: Den här artikeln handlar om lösningen på problemet där användaren inte kan ange en fakturerings- och leveransadress som är **different** och Vertex-adressverifiering är aktiverad.
exl-id: a481b044-3b74-4792-abc6-249a182c49e1
feature: B2B, Orders, Shipping/Delivery, Checkout
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Vertex Address Cleansing: olika adresser tillåts inte

I den här artikeln beskrivs lösningen på problemet där användaren inte kan ange en fakturerings- eller leveransadress som är **annorlunda** när Vertex-adressverifiering är aktiverat.

## Berörda produkter och versioner

* Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.5-p1

## Problem

<u>Steg som ska återskapas</u>:

1. Gå till Admin > **Lager** > **Konfiguration** > **Försäljning** > **Adressrensning**.
1. Välj *Aktiverad* i listrutan **Använd vertex Address Cleansing** och **Save Config**.
1. Gå till fronten som gäst och lägg till en produkt i kundvagnen.
1. Klicka på kundvagnsikonen och **Fortsätt till kassan**.
1. Fyll i adressfälten.
1. Välj önskad **leveransmetod** och klicka på **Nästa**.
1. Klicka på knappen **Nästa** igen.
1. Avmarkera **Min fakturerings- och leveransadress** **är densamma** och ange en ny faktureringsadress (som inte är Adress).
1. Klicka på knappen **Uppdatera** och sedan på **Uppdatera adress**.

<u>Förväntade resultat</u>:

Användaren ser olika fakturerings- och leveransadresser.

<u>Faktiska resultat</u>:

När användaren träffar på uppdateringen återställs fakturerings- och leveransadresserna till samma adress.

## Orsak

Verifieringen av vertex-adressen misslyckades.

## Lösning

Inaktivera Vertex Address-verifiering eller uppgradering till 2.4.0.

## Relaterad läsning

* [Problem med Adobe Commerce 2.4.0: Felmeddelande vid val av lokal betalningsmetod för vissa länder vid utcheckning](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0 Känt fel: 404-fel vid borttagning av poäng vid utcheckning av flera leveranser](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Adobe Commerce 2.4.0: fel vid visning av beställningar](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B Admin kan inte lägga till en konfigurerbar produkt att citera](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0: Braintree betalningsmetoder visas inte i kassan för flera adresser](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problem med Adobe Commerce 2.4.0 - uppdateringen av kundens aktiviteter fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problem med Adobe Commerce 2.4.0 - Export Tax Rates fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0: Knappen &quot;Lägg till markeringar i kundvagnen&quot; fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Adobe Commerce 2.4.0: Raw-meddelandedata visas i butiken](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 Känt fel: etiketten&quot;Refund&quot; saknas i Klarna](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Adobe Commerce 2.4.0: två knappar saknas på sidan Skapa ny order i Admin](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Problem med Adobe Commerce 2.4.0: När Braintree är aktiverat uppstår problemet med partiell faktura i Venmo](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Problem med Adobe Commerce 2.4.0: Felmeddelande vid val av lokal betalningsmetod för vissa länder vid utcheckning](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0: Amazon Pay aktiverat, betalningsmetoder saknas vid återgång till standardutcheckning](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Problem med Adobe Commerce 2.4.0: 2.4.0-installationen misslyckas med inaktuell arkivcache](/help/troubleshooting/installation-and-upgrade/magento-2-4-0-known-issue-2-4-0-installation-fails-with-outdated-stores-cache.md)
