---
title: 'Adobe Commerce 2.4.0: Amazon lönevillkor, inga betalningsmetoder'
description: Den här artikeln innehåller en lösning på ett Adobe Commerce 2.4.0-problem där betalningsmetoder saknas när man använder **Återgå till standardutcheckning** efter att Amazon betalat.
exl-id: efd792c7-8970-4366-b9d1-4bf284ea96db
feature: B2B, Orders, Payments
role: Developer
source-git-commit: 05297c82b292b8ccc88018c58e991bd3a32d6ffa
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Amazon lönevillkor, inga betalningsmetoder

Den här artikeln innehåller en lösning på ett känt problem i Adobe Commerce 2.4.0 där betalningsmetoder saknas när kunder använder **Återgå till standardutcheckning**, efter att de aktiverat Amazon-betalning.

## Berörda produkter och versioner

Adobe Commerce lokalt och Adobe Commerce på molninfrastrukturen v2.3.5.p1 och v2.4.0

<u>Steg att återskapa:</u>

1. Navigera till butiken.
1. Lägg alla artiklar i kundvagnen och fortsätt till kassan.
1. Logga in på ditt Amazon Pay-konto.
1. Välj en adress och fortsätt till utcheckningen.
1. Klicka på **Återgå till standardutcheckningen**.
1. Gå till kassan.

<u>Förväntade resultat:</u>

Betalningsmetoder ska visas när utcheckningen har startats om.

<u>Faktiska resultat:</u>

Betalningsmetoder saknas.

## Lösning

En upplösning planeras för 2.4.1.

## Relaterade läsningar i vår kunskapsbas:

* [Problem med Adobe Commerce 2.4.0: Felmeddelande vid val av lokal betalningsmetod för vissa länder vid utcheckning](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0 B2B Admin kan inte lägga till en konfigurerbar produkt att citera](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0: Braintree betalningsmetoder visas inte i kassan för flera adresser](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
