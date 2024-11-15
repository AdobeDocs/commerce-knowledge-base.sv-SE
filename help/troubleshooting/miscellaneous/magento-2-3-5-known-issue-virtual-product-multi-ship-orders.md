---
title: "Adobe Commerce 2.3.5 known issue: virtual product multi-ship orders"
description: I den här artikeln förklaras ett känt fel i Adobe Commerce 2.3.5 där en beställning som innehåller en virtuell produkt för flera leveranser inte behandlas korrekt.
exl-id: 34ce79a2-5157-492b-8ee4-bdc09aae0c40
feature: Orders, Products, Shipping/Delivery
role: Developer
source-git-commit: b3d39e6b02728f05f046adf7be94ffacbca944d5
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Adobe Commerce 2.3.5: Problem med beställningar av virtuella produkter för flera leveranser

I den här artikeln förklaras ett känt fel i Adobe Commerce 2.3.5 där en beställning som innehåller en virtuell produkt för flera leveranser inte behandlas korrekt.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.3.5
* Adobe Commerce om molninfrastruktur 2.3.5

## Problem

<u>Steg som ska återskapas</u>:

1. I butiken lägger du till fysiska och virtuella produkter i kundvagnen.
1. Gå till kassan och välj **Checka ut med flera adresser**.
1. Lägg till all nödvändig information och beställ.

<u>Förväntat resultat</u>:

Alla produkter beställs.

<u>Faktiskt resultat</u>:

Ordningen för den virtuella produkten är tom.

## Korrigera

En programfix kommer att finnas i Adobe Commerce 2.3.6, som kommer att släppas tredje kvartalet 2020.

## Relaterad läsning

I vår kunskapsbas:

* [Produktjämförelse - känt fel i Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
* [Ett problem har uppstått med produktantalet för gruppåtgärd i Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)
* [Patch for Amazon Pay checkout issue in Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)

I vår utvecklardokumentation:

* [Versionsinformation om Adobe Commerce 2.3.5](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
