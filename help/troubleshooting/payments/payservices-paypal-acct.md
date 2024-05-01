---
title: PayPal-sandlådekontot har inte verifierats
description: I den här artikeln förklaras varför ditt PayPal-sandlådekonto för Betalningstjänster kanske inte kan verifieras, vilket gör att du inte kan slutföra introduktionen av sandlådor.
exl-id: 05ce130d-6dfe-4834-bdfc-837902100118
feature: Customer Service, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# PayPal-sandlådekontot har inte verifierats

I den här artikeln förklaras varför ditt PayPal-sandlådekonto för Betalningstjänster kanske inte kan verifieras, vilket gör att du inte kan slutföra introduktionen av sandlådor.

## Berörda produkter och versioner

* [Betalningstjänster](https://marketplace.magento.com/magento-payment-services.html) är nu kompatibelt med Adobe Commerce version 2.4.0 till 2.4.4.

## Problem

Våra [dokumentation om introduktion](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html) instruerar dig att registrera dig för ett PayPal-konto, logga in på PayPal-utvecklarkontot och sedan skapa ett sandlådekonto. Om du väljer att skapa ett nytt konto under introduktionen i popup-fönstret PayPal-introduktion, kommer PayPal inte att kunna verifiera ditt sandlådekonto och du kommer inte att kunna slutföra introduktionen.

<u>Steg som ska återskapas</u>:

1. Du [installera betaltjänster](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) och [konfigurera dina Commerce-tjänster](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-commerce-services).
1. Navigera till **Betalningstjänster** i Admin och [starta introduktion av sandlåda](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html).
1. I popup-fönstret PayPal-introduktion som visas skapar du ett nytt Business-konto (i stället för [logga in med ett tidigare skapat PayPal-sandlådekonto](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) under introduktionen.
1. PayPal-introduktionen har slutförts.
1. Du ser ett meddelande i Admin om att dina sandlådebetalningar är väntande och att du måste bekräfta din e-postadress hos PayPal för att kunna slutföra introduktionen.

   Du fick inget bekräftelsemeddelande eftersom PayPal inte kunde verifiera din e-postadress.

## Orsak

PayPal kommer inte att kunna verifiera ditt sandlådekonto och du kommer inte att kunna slutföra introduktionen av sandlådor (vilket betyder att du inte kan acceptera betalningar eller testa sandlådeläget) om du skapar ditt sandlådekonto före ditt PayPal-konto.

## Lösning

1. Använda ett sandlådekonto som skapats i [PayPal Developer](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account) Portal.
1. Klicka [återställ sandlåda](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) och starta om din introduktion till sandlådan.
1. [Kontakta supporten](mailto:payment-services-support@adobe.com) om du inte kan åtgärda dina kontoproblem så att du kan återuppta introduktionen och acceptera betalningar.
