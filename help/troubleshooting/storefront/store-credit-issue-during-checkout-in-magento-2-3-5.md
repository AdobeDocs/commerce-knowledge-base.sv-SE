---
title: Store credit issue in checkout in Adobe Commerce 2.3.5
description: I den här artikeln beskrivs ett sätt att kringgå det kända butikskreditrelaterade problemet vid utcheckning i Adobe Commerce 2.3.5, där kunderna får felmeddelanden vid utcheckning efter att de har valt och senare tagit bort butikskreditanvändningen. En permanent programfix finns i Adobe Commerce 2.3.6.
exl-id: a0cca226-4d95-40b3-bd37-f13d28591366
feature: Checkout, Orders, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Store credit issue in checkout in Adobe Commerce 2.3.5

I den här artikeln beskrivs ett sätt att kringgå det kända butikskreditrelaterade problemet vid utcheckning i Adobe Commerce 2.3.5, där kunderna får felmeddelanden vid utcheckning efter att de har valt och senare tagit bort butikskreditanvändningen. En permanent programfix finns i Adobe Commerce 2.3.6.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.3.5
* Adobe Commerce om molninfrastruktur 2.3.5

## Problem

<u>Steg som ska återskapas</u>:

1. Kunden lägger till produkter i kundvagnen och fortsätter till kassan.
1. Kunden anger butikskrediten som betalningsmetod.
1. Kunden tar bort butikskrediten och ändrar betalningsmetoden.
1. Kunderna går vidare till kassan.

<u>Förväntade resultat</u>:

All orderinformation visas korrekt.

<u>Faktiska resultat</u>:

Adobe Commerce genererar ett fel i ordersammanfattningsdelen på ordersidan.

## Lösning

Kunderna kan uppdatera ordersidan och informationen i ordersammanfattningen läses in korrekt. En programfix kommer att finnas i Adobe Commerce 2.3.6, som kommer att släppas tredje kvartalet 2020.

## Relaterad läsning

Artiklar för Adobe Commerce 2.3.5 Kända fel i vår kunskapsbas:

* [Beställningar för flera leveranser med en virtuell produkt som inte har bearbetats korrekt i Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)

* [Problem med betalningsmetod i Adobe Commerce för molninfrastruktur och Adobe Commerce lokal 2.3.5 och 2.3.5-p1](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)

* [Adobe Commerce uppmanar sina kunder att logga in, men erbjuder en ogiltig länk](/help/troubleshooting/known-issues-patches-attached/magento-prompts-customers-log-in-invalid-link.md)

* [Ett problem har uppstått med produktantalet för gruppåtgärd i Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)

* [Patch for Amazon Pay checkout issue in Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)

* [Produktjämförelse i Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)

I vår utvecklardokumentation:

* [Adobe Commerce 2.3.5 Kända fel](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
