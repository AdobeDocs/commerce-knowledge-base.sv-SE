---
title: "Adobe Commerce 2.4.0: uppdatering av kundens aktiviteter fungerar inte"
description: Den här artikeln innehåller en lösning på ett problem som är känt i Adobe Commerce 2.4.0 när en admin-användare skapar en beställning för en kund och uppdateringsknapparna på aktivitetspanelen inte fungerar.
exl-id: 50048e9f-6009-4db5-ae4a-c35a84cec265
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Uppdatering av kundens aktiviteter fungerar inte

Den här artikeln innehåller en lösning på ett problem som är känt i Adobe Commerce 2.4.0 när en admin-användare skapar en beställning för en kund och uppdateringsknapparna på aktivitetspanelen inte fungerar.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.4.0
* Adobe Commerce om molninfrastruktur 2.4.0

## Problem

<u>Steg som ska återskapas</u>:

1. Gå till **Admin Panel** > **Försäljning** > **Beställningar**.
1. Klicka på **Skapa ny order** -knappen.
1. Välj den skapade kunden.
1. Gå till butiken som kund.
1. Gå till **Produkt** sida. Klicka på **Uppdatera** på **Nyligen visade produkter** avsnitt i **Kundens aktiviteter**.
1. Gå tillbaka till butiken.
1. Placera en order med de produkter du har skapat.
1. Gå tillbaka till **Admin Panel** och klicka på **Uppdatera** knappen på **Senast beställda objekt** avsnitt i **Kundens aktiviteter**.
1. Gå tillbaka till butiken. Lägg till den skapade produkten i **Jämförelselista**.
1. Gå tillbaka till **Admin Panel**. Klicka på **Uppdatera** knappen på **Produkter i jämförelselista** avsnitt i **Kundens aktiviteter**.
1. Gå tillbaka till butiken.
1. Ta bort den skapade produkten från **Jämförelselista**.
1. Gå tillbaka till **Admin Panel**.
1. Klicka på **Uppdatera** knappen på **Nyligen jämförda produkter** avsnitt i **Kundens aktiviteter**.
1. Gå tillbaka till butiken.

<u>Förväntade resultat</u>:

Namnet på produkten ska finnas i **Nyligen visade produkter**, **Senast beställda objekt**, **Produkter i jämförelselista** och **Nyligen jämförda produkter** -avsnitt.

<u>Faktiska resultat</u>:

Sidan rullas upp varje gång **Uppdatera** klickas på knappen. Namnet på produkten visas inte i rätt avsnitt.

## Lösning

En tillfällig lösning är att administratören kan uppdatera **Kundens aktiviteter** genom att klicka på **Uppdatera ändringar** längst ned i sidlisten. Problemet är planerat att åtgärdas i Adobe Commerce 2.4.1-patchen.

![mceclip0.png](assets/mceclip0.png)

## Relaterad läsning

* [Adobe Commerce 2.4.0: Braintree betalningsmetoder visas inte i kassan för flera adresser](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problem med att skapa etiketter i Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Adobe Commerce 2.4.0: Raw-meddelandedata visas i butiken](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0: Exportavgifter fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0: Knappen &quot;Lägg till markeringar i kundvagnen&quot; fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
