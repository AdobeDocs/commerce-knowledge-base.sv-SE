---
title: Kreditkortet underkändes vid betalningar i sandlådemiljö
description: I den här artikeln förklaras varför ett testkreditkort inte fungerar i en sandlådemiljö med PayPal-API:er.
exl-id: 65fd08e0-eefc-47f3-8964-bef3610e6182
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Kreditkortet underkändes vid betalningar i sandlådemiljö

I den här artikeln förklaras varför ett testkreditkort inte fungerar i en sandlådemiljö med PayPal-API:er.

## Berörda produkter och versioner


* Adobe Commerce 2.4.0 - 2.4.4, alla driftsättningsalternativ, med [Betalningstjänster](https://marketplace.magento.com/magento-payment-services.html)

## Problem

När du använder ett test-kreditkort för Visa `4111 1111 1111 1111` från PayPal, ibland misslyckas det på grund av PayPal-principer med följande fel:

```terminal
Error happened when processing the request. Please try again later.
```

## Orsak

Det här felet visas när PayPal flaggar ett specifikt testkreditkortsnummer för bedrägeri. Det beror på att det är ett testkreditkortsnummer som används av alla runt om i världen som testar med PayPal API:er.

## Lösning

Använd ett annat testkreditkort. Om du vill generera ett modellkreditkort kan du använda för att testa:

1. Gå till PayPal Developer Portal [Kreditkortsgenerator](https://developer.paypal.com/developer/creditCardGenerator/) sida.
1. Logga in på PayPal Developer Portal Dashboard.
1. Generera ett testkreditkort.
