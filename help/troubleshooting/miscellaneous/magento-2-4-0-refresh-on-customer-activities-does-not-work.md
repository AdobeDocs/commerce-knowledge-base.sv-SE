---
title: 'Adobe Commerce 2.4.0: Uppdatering av kundens aktiviteter fungerar inte'
description: Den här artikeln innehåller en lösning på ett problem som är känt i Adobe Commerce 2.4.0 när en admin-användare skapar en beställning för en kund och uppdateringsknapparna på aktivitetspanelen inte fungerar.
exl-id: 50048e9f-6009-4db5-ae4a-c35a84cec265
feature: Configuration
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Uppdatering av kundens aktiviteter fungerar inte

Den här artikeln innehåller en lösning på ett problem som är känt i Adobe Commerce 2.4.0 när en admin-användare skapar en beställning för en kund och uppdateringsknapparna på aktivitetspanelen inte fungerar.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.4.0
* Adobe Commerce om molninfrastruktur 2.4.0

## Problem

<u>Steg som ska återskapas</u>:

1. Gå till **administrationspanelen** > **Försäljning** > **Beställningar**.
1. Klicka på knappen **Skapa ny ordning** .
1. Välj den skapade kunden.
1. Gå till butiken som kund.
1. Gå till sidan **Produkt**. Klicka på knappen **Uppdatera** i avsnittet **Senast visade produkter** i **Kundens aktiviteter**.
1. Gå tillbaka till butiken.
1. Placera en order med de produkter du har skapat.
1. Gå tillbaka till **administrationspanelen** och klicka på knappen **Uppdatera** i avsnittet **Senast beställda objekt** i **Kundens aktiviteter**.
1. Gå tillbaka till butiken. Lägg till den skapade produkten i **jämförelselistan**.
1. Gå tillbaka till **Admin Panel**. Klicka på knappen **Uppdatera** i avsnittet **Produkter i jämförelselista** i **Kundens aktiviteter**.
1. Gå tillbaka till butiken.
1. Ta bort den skapade produkten från **jämförelselistan**.
1. Gå tillbaka till **Admin Panel**.
1. Klicka på knappen **Uppdatera** i avsnittet **Nyligen jämförda produkter** i **Kundens aktiviteter**.
1. Gå tillbaka till butiken.

<u>Förväntade resultat</u>:

Namnet på produkten ska visas i avsnittet **Senast visade produkter**, **Senast beställda objekt**, **Produkter i jämförelselista** och **Nyligen jämförda produkter**.

<u>Faktiska resultat</u>:

Sidan rullas upp varje gång någon klickar på knappen **Uppdatera**. Namnet på produkten visas inte i rätt avsnitt.

## Lösning

En tillfällig lösning är att administratörsanvändaren kan uppdatera **kundens aktiviteter** genom att klicka på knappen **Uppdatera ändringar** längst ned i sidlisten. Problemet är planerat att åtgärdas i Adobe Commerce 2.4.1-patchen.

![mceclip0.png](assets/mceclip0.png)

## Relaterad läsning

* [Adobe Commerce 2.4.0: Braintree betalningsmetoder visas inte i kassan för flera adresser](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0: Exportavgifter fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0: Knappen &quot;Lägg till markeringar i kundvagnen&quot; fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
