---
title: Ett problem har uppstått med produktantalet för gruppåtgärd i Adobe Commerce 2.3.5
description: I den här artikeln beskrivs ett känt problem med Adobe Commerce 2.3.5, där meddelandet en handlare får efter en gruppåtgärd i Admin innehåller fel antal påverkade objekt.
exl-id: 3ede15d4-4c39-442a-8784-2d5e6650fe67
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Ett problem har uppstått med produktantalet för gruppåtgärd i Adobe Commerce 2.3.5

I den här artikeln beskrivs ett känt problem med Adobe Commerce 2.3.5, där meddelandet en handlare får efter en gruppåtgärd i Admin innehåller fel antal påverkade objekt.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.3.5
* Adobe Commerce lokal 2.3.5

## Problem

Systemmeddelandet som visas av Adobe Commerce efter en satsåtgärd (till exempel en massproduktuppdatering eller import/export) visar antalet 0 i stället för ett korrekt antal produkter som påverkas av gruppåtgärden.

## Korrigera

En programfix kommer att finnas i Adobe Commerce 2.3.6, som kommer att släppas tredje kvartalet 2020.

## Relaterad läsning

* Adobe Commerce Support Knowledge Base-artiklar om Adobe Commerce 2.3.5:
   * [Beställningar för flera leveranser med en virtuell produkt som inte har bearbetats korrekt i Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)
   * [Produktjämförelse - känt fel i Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
   * [Problem med betalningsmetod i Adobe Commerce för molninfrastruktur och Adobe Commerce lokal 2.3.5 och 2.3.5-p1](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)
   * [Patch for Amazon Pay checkout issue in Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)
   * [Kända fel i Adobe Commerce 2.3.5 i utvecklardokumentationen](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
