---
title: Betalningsmetoder som inte visas vid utcheckning med flera adresser
description: I den här artikeln förklaras att de flesta betalningsmetoder inte visas vid utcheckning när flera leveransadresser anges, eftersom funktionen bara implementeras för Cybersource.
exl-id: 68a9ee77-d0ef-43c5-9667-6d099b797666
feature: Checkout, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Betalningsmetoder som inte visas vid utcheckning med flera adresser

I den här artikeln förklaras att de flesta betalningsmetoder inte visas vid utcheckning när flera leveransadresser anges, eftersom funktionen bara implementeras för Cybersource.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.x.x
* Adobe Commerce i molninfrastruktur 2.x.x

>[!NOTE]
>
>Adobe Commerce Cybersource-betalningsintegration har tagits bort sedan 2.3.3 och kommer att tas bort helt i 2.4.0. Använd det [officiella tillägget](https://marketplace.magento.com/cybersource-global-payment-management.html) från Marketplace i stället.

## Problem

<u>Förutsättningar</u>: Aktivera och konfigurera betalningsmetoder för PayPal och Cybersource i Commerce Admin och aktivera Multishipping för din butik.

<u>Steg som ska återskapas</u>:

1. Lägg flera produkter i kundvagnen i butiken.
1. Gå till kundvagnssidan.
1. Klicka på **Checka ut med flera adresser**.
1. Logga in eller skapa konto.
1. Dela upp produkter mellan adresserna på sidan Leverera till flera adresser.
1. Klicka på **Gå till leveransinformation**.
1. Välj leveransmetoder för varje leverans.
1. Klicka på **Fortsätt till faktureringsinformation**.

<u>Förväntat resultat</u>: PayPal och Cybersource är tillgängliga som betalningsalternativ.

<u>Faktiskt resultat</u>: Endast Cybersource visas som tillgängligt betalningsalternativ.

## Orsak

Cybersource är för närvarande den enda live-betalningsmetoden som stöds för utcheckning av flera leveranser, från version 2.2.4. Stöd för flera leveranser kommer sannolikt att skapas för varje betalningsmetod, en i taget. Inga exakta datum eller releasenummer kan anges för tillfället.
