---
title: Problem med Adobe Commerce 2.4.0 - Export Tax Rates fungerar inte
description: Den här artikeln innehåller en lösning på ett Adobe Commerce 2.4.0-problem där knappen **Export Tax Rates** inte fungerar.
exl-id: 29a34a1f-d23a-43cb-ac1f-8711ce25fa6c
feature: Data Import/Export, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Problem med Adobe Commerce 2.4.0 - Export Tax Rates fungerar inte

Den här artikeln innehåller en lösning på ett Adobe Commerce 2.4.0-problem där **Exportskattesatser** fungerar inte.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.4.0
* Adobe Commerce lokal 2.4.0

## Problem

<u>Steg som ska återskapas:</u>

1. Gå till Commerce Admin Panel > **Lager** > **Skatteregler**.
1. Klicka på **Lägg till ny momsregel** -knappen.
1. Klicka på texten i **Exportskattesatser** -knappen.

   ![magento_export_tax_rates.png](assets/mceclip0.png)

<u>Förväntat resultat</u>:

A `tax_rates.csv` nedladdningar med momssatser.

<u>Faktiskt resultat</u>:

Ingen CSV-fil hämtas.

## Lösning

Lösning:

Klicka på den nedre vänstra kanten av **Exportskattesatser** för att exportera `tax_rates.csv` -fil.

![magento_export_tax_rates.png](assets/mceclip1.png)

Vi planerar att åtgärda problemet i en 2.4.1- patch.

## Relaterad läsning

I vår kunskapsbas:

* [Adobe Commerce 2.4.0: Braintree betalningsmetoder visas inte i kassan för flera adresser](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md).
* [Problem med att skapa etiketter i Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md).
* [Problem med Adobe Commerce 2.4.0 - uppdateringen av kundens aktiviteter fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md).
* [Adobe Commerce 2.4.0: Raw-meddelandedata visas i butiken](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md).
* [Adobe Commerce 2.4.0: Knappen &quot;Lägg till markeringar i kundvagnen&quot; fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md).
