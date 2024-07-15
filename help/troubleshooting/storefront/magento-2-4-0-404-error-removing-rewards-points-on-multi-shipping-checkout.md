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

I den här artikeln beskrivs en lösning på ett känt fel i Adobe Commerce 2.4.0 för ett *404 Hittades inte*-webbsidesfel när belöningspunkter tas bort från en utcheckningssida för flera leveranser. För närvarande visas sidan *404 Hittades inte* på den utcheckade sidan för flera leveranser i stället för att belöningspoäng annulleras om du försöker ta bort belöningspoäng som användes för att betala för en order. Problemet åtgärdas i en patchversion av Adobe Commerce 2.4.1.

## Berörda produkter och versioner

* Adobe Commerce 2.4.0 (alla distributionsmetoder)

## Problem

<u>Steg som ska återskapas</u>

1. Navigera till butiken och logga in som kund.
1. Lägg till minst två produkter i **kundvagnen**.
1. Öppna **Mini-Cart**.
1. Klicka på länken **Visa och redigera kundvagn**.
1. Klicka på länken **Checka ut med flera adresser**.
1. Välj leveransadresser på sidan **Leverera till flera adresser**.
1. Klicka på knappen **Gå till leveransinformation**.
1. Välj **platt hastighet - fast leveransmetod** för varje adress.
1. Klicka på knappen **Fortsätt till faktureringsinformation**.
1. Markera kryssrutan **Använd dina belöningspunkter** på sidan **Faktureringsinformation**.
1. Klicka på knappen **Gå till Granska din beställning**.
1. Klicka på länken **Ta bort** för en adress om du vill ta bort belöningspunkter.

<u>Förväntade resultat</u>

* Sidan **Kundvagn** ska visas.
* *Du har tagit bort belöningspoängen från den här ordern.Meddelandet* ska visas.

<u>Faktiskt resultat</u>

Felsidan *404 Hittades inte* visas.

## Tillfällig lösning

Du kan lösa problemet genom att låta köparen navigera tillbaka till **kundvagnen** och ta bort belöningspoängen från webbsidan **Kundvagn**. Problemet förväntas bli åtgärdat i Adobe Commerce version 2.4.1, som ska släppas 4:e kvartalet 2020.

## Relaterad läsning

* [Problem med Adobe Commerce 2.4.0 - uppdateringen av kundens aktiviteter fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 Known Issue: Raw message data display on Storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 Känt fel: Exportskattesatser fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B Admin kan inte lägga till en konfigurerbar produkt att citera](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0 Känt fel: Visningsfel för beställningar](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
