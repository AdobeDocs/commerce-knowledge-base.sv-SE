---
title: "Adobe Commerce 2.4.0: 404 error removing rewards points on multi-shipping checkout"
description: I den här artikeln finns en lösning på ett känt fel i Adobe Commerce 2.4.0 för ett fel på webbsidan "*404 Hittades inte*" när du tar bort belöningspunkter på en utcheckningssida för flera leveranser. På kassan för flera leveranser visas för närvarande sidan "*404 Hittades inte*" i stället för att belöningspoängen annullerades när belöningspoäng som användes för att betala en order skulle tas bort. Problemet åtgärdas i en patchversion av Adobe Commerce 2.4.1.
exl-id: 59de4b3d-af28-4ae8-8f55-4ec958e6ee8b
feature: B2B, Checkout, Orders, Rewards, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: 404 error removing rewards points on multi-shipping checkout

I den här artikeln beskrivs en lösning på ett känt problem i Adobe Commerce 2.4.0 för en *404 Hittades inte*&quot; webbsidesfel vid borttagning av belöningspunkter på en utcheckningssida för flera leveranser. För närvarande, på kassan för flera leveranser, en &quot;*404 Hittades inte* &quot; visas i stället för att belöningspoäng annulleras. Problemet åtgärdas i en patchversion av Adobe Commerce 2.4.1.

## Berörda produkter och versioner

* Adobe Commerce 2.4.0 (alla distributionsmetoder)

## Problem

<u>Steg som ska återskapas</u>

1. Navigera till butiken och logga in som kund.
1. Lägg till minst två produkter i **Kundvagn**.
1. Öppna **Mini-Cart**.
1. Klicka på **Visa och redigera kundvagn** länk.
1. Klicka på **Checka ut med flera adresser** länk.
1. Välj leveransadresser på **Leverera till flera adresser** sida.
1. Klicka på **Gå till leveransinformation** -knappen.
1. Välj **Schablonbelopp - fast leveranssätt** för varje adress.
1. Klicka på **Fortsätt till faktureringsinformation** -knappen.
1. Kontrollera **Använd dina belöningspoäng** kryssrutan på **Faktureringsinformation** sida.
1. Klicka på **Gå till Granska din beställning** -knappen.
1. Klicka på **Ta bort** länk för en adress för att ta bort belöningspoängen.

<u>Förväntade resultat</u>

* The **Kundvagn** sidan ska visas.
* The &quot;*Du har tagit bort belöningspoängen från den här ordern.* &quot; ska visas.

<u>Faktiskt resultat</u>

A &quot;*404 Hittades inte* &quot; visas.

## Tillfällig lösning

Den tillfälliga lösningen är att få köparen att gå tillbaka till **Kundvagn** och ta bort belöningspoängen från **Kundvagn** webbsida. Problemet förväntas bli åtgärdat i Adobe Commerce version 2.4.1, som ska släppas 4:e kvartalet 2020.

## Relaterad läsning

* [Problem med Adobe Commerce 2.4.0 - uppdateringen av kundens aktiviteter fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 Known Issue: Raw message data display on Storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 Känt fel: Exportskattesatser fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B Admin kan inte lägga till en konfigurerbar produkt att citera](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0 Känt fel: Visningsfel för beställningar](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
