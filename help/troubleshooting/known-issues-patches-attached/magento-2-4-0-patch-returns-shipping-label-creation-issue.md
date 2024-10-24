---
title: "Adobe Commerce 2.4.0 patch: returns shipping label creation issue"
description: Den här artikeln innehåller en patch för det kända problemet med Adobe Commerce 2.4.0 när det uppstår problem med att skriva ut en fraktsetikett för kundreturer.
exl-id: f78f8d7e-29e9-4d6c-83f6-cd5afa1d7d9c
feature: B2B, Orders, Returns, Communications, Shipping/Delivery
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 patch: returnerar problem med att skapa etiketter för frakt

Den här artikeln innehåller en patch för det kända problemet med Adobe Commerce 2.4.0 när det uppstår problem med att skriva ut en fraktsetikett för kundreturer.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.4.0
* Adobe Commerce lokal 2.4.0

## Problem

<u>Steg att återskapa:</u>

1. Gör en beställning med någon av följande metoder: FedEx, DHL, UPS och USPS.
1. Skapa och auktorisera returer för den här ordern.
1. Öppna en auktoriserad sida för **returinformation** och klicka på knappen **Skapa leveransetikett** .
1. Välj leveranssätt, lägg till en produkt i ett paket och klicka på Spara.

<u>Förväntat resultat:</u>

En leveransetikett har skapats och du ser ett meddelande: *Du har skapat en leveransetikett.*

<u>Faktiskt resultat:</u>

Sidan **Returinformation** är skadad och ett felmeddelande visas på sidan Returinformation: *Allmänna informationsändringar har gjorts i det här avsnittet som inte har sparats. Fliken innehåller ogiltiga data*.

## Lösning

Använd [patch](assets/MC-35984-2.4.0-CE-composer.patch.zip) som anges i den här artikeln.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[MC-35984-2.4.0-CE-Composer.patch](assets/MC-35984-2.4.0-CE-composer.patch.zip)

Korrigeringen kan också laddas ned både `.git` och `.composer` på sidan [Adobe Commerce Downloads](https://magento.com/tech-resources/download) under **Patchar** i den vänstra kolumnnavigeringen. Sök efter patchen MC-35984.

## Så här sätter du på plåstret

Instruktioner finns i [Använda en dispositionsruta från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) på vår kunskapssida med supportfrågor.

## Relaterade läsningar i vår kunskapsbas:

* [Adobe Commerce 2.4.0: Raw-meddelandedata visas i butiken](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0: Exportavgifter fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0: Knappen &quot;Lägg till markeringar i kundvagnen&quot; fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Adobe Commerce 2.4.0: Braintree betalningsmetoder visas inte i kassan för flera adresser](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0 B2B Admin kan inte lägga till en konfigurerbar produkt att citera](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0: fel vid visning av beställningar](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
