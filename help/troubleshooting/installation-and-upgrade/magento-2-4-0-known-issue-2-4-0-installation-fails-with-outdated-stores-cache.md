---
title: Installationen av Adobe Commerce 2.4.0 misslyckas med inaktuell arkivcache
description: "I den här artikeln finns en lösning på problemet där din Adobe Commerce 2.4.0-installation misslyckas med felmeddelandet: *Standardwebbplatsen är inte definierad. Ange webbplatsen och försök igen.* visas i konsolen."
exl-id: 0680199b-7e47-4a8c-91fe-9f6c32839a0e
feature: B2B, Cache, Console, Install, Upgrade
role: Developer
source-git-commit: 2bba3af8919e1db8482764b8d688f95e606c2683
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# Installationen av Adobe Commerce 2.4.0 misslyckas med inaktuell arkivcache

I den här artikeln finns en lösning på problemet där din Adobe Commerce 2.4.0-installation misslyckas med felmeddelandet: *Standardwebbplatsen är inte definierad. Ange webbplatsen och försök igen.* visas i konsolen.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.4.0
* Adobe Commerce lokal 2.4.0

## Problem

<u>Förutsättningar:</u>
Ett tillägg från tredje part med beroenden på API:er för butiksmodulen i CLI-kommandon har konfigurerats enligt kraven i `composer.json` . Detta gör att installationen av Adobe Commerce 2.4.0 misslyckas med ett felmeddelande: *Standardwebbplatsen är inte definierad. Ange webbplatsen och försök igen.* visas i konsolen.

## Orsak

Problemet visas för tredjepartstillägg som är beroende av butiker i sina CLI-kommandon. En av dem är Amazon Sales Channeler.

## Lösning

Före installationen av Adobe Commerce 2.4.0 måste handlarna

1. Ta bort de här tredjepartstilläggen från `composer.json`.
1. Installera Adobe Commerce utan tillägg.
1. Lägg till tilläggen efter installationen.

Problemet kommer att åtgärdas i version 2.4.1.

## Relaterade läsningar i vår kunskapsbas:

* [Adobe Commerce 2.4.0 Känt fel: etiketten&quot;Refund&quot; saknas i Klarna](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Adobe Commerce 2.4.0: två knappar saknas på sidan Skapa ny order i Admin](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Adobe Commerce 2.4.0, 2.4.1: Aktivera problemet med partiella fakturor i Braintree Venmo](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Problem med Adobe Commerce 2.4.0: Felmeddelande vid val av lokal betalningsmetod för vissa länder vid utcheckning](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0: Amazon Pay aktiverat, betalningsmetoder saknas vid återgång till standardutcheckning](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Adobe Commerce 2.4.0 Känt fel: 404-fel vid borttagning av poäng vid utcheckning av flera leveranser](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Adobe Commerce 2.4.0: fel vid visning av beställningar](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B Admin kan inte lägga till en konfigurerbar produkt att citera](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0: Braintree betalningsmetoder visas inte i kassan för flera adresser](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problem med att skapa etiketter i Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Problem med Adobe Commerce 2.4.0 - uppdateringen av kundens aktiviteter fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problem med Adobe Commerce 2.4.0 - Export Tax Rates fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0: Knappen &quot;Lägg till markeringar i kundvagnen&quot; fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Adobe Commerce 2.4.0: Raw-meddelandedata visas i butiken](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
