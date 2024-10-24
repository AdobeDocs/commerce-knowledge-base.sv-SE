---
title: Problem med Adobe Commerce 2.4.0 - Export Tax Rates fungerar inte
description: Den här artikeln innehåller en lösning på ett Adobe Commerce 2.4.0-problem där knappen **Export Tax Rates** inte fungerar.
exl-id: 29a34a1f-d23a-43cb-ac1f-8711ce25fa6c
feature: Data Import/Export, Orders
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Problem med Adobe Commerce 2.4.0 - Export Tax Rates fungerar inte

Den här artikeln innehåller en lösning på ett känt problem i Adobe Commerce 2.4.0 där knappen **Exportera momssatser** inte fungerar.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.4.0
* Adobe Commerce lokal 2.4.0

## Problem

<u>Steg att återskapa:</u>

1. Gå till Commerce Admin Panel > **Stores** > **Tax Rules**.
1. Klicka på knappen **Lägg till ny momsregel**.
1. Klicka på texten för knappen **Exportera momssatser**.

   ![magento_export_tax_rates.png](assets/mceclip0.png)

<u>Förväntat resultat</u>:

En `tax_rates.csv`-fil laddas ned med momssatser.

<u>Faktiskt resultat</u>:

Ingen CSV-fil hämtas.

## Lösning

Lösning:

Klicka på den nedre vänstra kanten av knappen **Exportera momssatser** för att exportera filen `tax_rates.csv`.

![magento_export_tax_rates.png](assets/mceclip1.png)

Vi planerar att åtgärda problemet i en 2.4.1- patch.

## Relaterad läsning

I vår kunskapsbas:

* [Ett känt fel uppstod i Adobe Commerce 2.4.0: Braintree betalningsmetoder visas inte i kassan för flera adresser](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md).
* [Problem med Adobe Commerce 2.4.0 - Uppdatering av kundens aktiviteter fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md).
* [Ett känt fel uppstod i Adobe Commerce 2.4.0: visning av råmeddelandedata i store](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md).
* [Problem med Adobe Commerce 2.4.0: Knappen Lägg till markeringar i kundvagnen fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md).
