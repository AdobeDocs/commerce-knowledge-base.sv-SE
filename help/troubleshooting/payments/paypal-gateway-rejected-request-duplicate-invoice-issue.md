---
title: PayPal-gateway avvisade begäran - dubblettfakturautleverans
description: Den här artikeln innehåller en korrigering för PayPal-gatewayens nekade begäran - dubblettfakturaproblem.
exl-id: b6c4ede1-97a5-4db3-9b05-ab979cf809b3
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# PayPal-gateway avvisade begäran - dubblettfakturautleverans

Den här artikeln innehåller en korrigering för PayPal-gatewayens nekade begäran - dubblettfakturaproblem.

När kunden skickar in en betalning kan ett fel uppstå för en dubblettfaktura:

>PayPal-gatewayen har avvisat begäran. Betalning har redan gjorts för detta faktura-ID (\#10412: Duplicera faktura)

Problemet uppstår när fakturor med samma ID skickas till PayPal flera gånger.

Du kan lösa problemet genom att tillåta flera betalningar per faktura-ID i PayPals Inställningar för betalningsmottagning. Om detta ändras accepteras betalningar utan felmeddelanden i PayPal, även för fakturor med duplicerade ID:n.

## Berörda versioner

* Adobe Commerce lokala, alla versioner
* Adobe Commerce om molninfrastruktur, alla versioner

## Problem

När kunderna skickar in betalningar visas felmeddelandet:

```
... main.CRITICAL: Exception message: PayPal gateway has rejected request. Payment has already been made for this InvoiceID (#10412: Duplicate invoice).
```

PayPal kan inte bearbeta betalningen och slutföra ordern.

## Orsak

Felmeddelandet visas när fakturor med samma ID skickas till PayPal flera gånger.

Det här kan hända om du använder samma inloggningsuppgifter för flera Adobe Commerce-platser (till och med för lokala miljöer och mellanlagringsmiljöer). Följande scenarier kan vara speciella:

* Flera butiker skickar fakturor till PayPal och använder samma faktura-ID
* En ny butik skickar en faktura med ett ID som tidigare har skickats av en gammal butik

Som standard tillåter PayPal inte bearbetning för samma faktura två gånger.

## Lösning

Ändra din PayPal-profil så att du kan använda flera betalningar per faktura-ID. Du måste göra dessa ändringar via PayPal.

1. Logga in på ditt konto på [https://www.paypal.com](https://www.paypal.com/).
1. Klicka **Profil** > **Profil och inställningar** (övre högra hörnet).
1. Gå till **Mina säljverktyg**.
1. Navigera till **Få betalt och hantera mina risker** > **Blockera betalningar** och klicka **Uppdatera**.
1. **Försäljningsinställningar**, klicka **Inställningar för betalningsmottagning**.
1. Under **Blockera olycksfallsbetalningar**, välja **Nej, tillåt flera betalningar per faktura-ID**.    ![paypal_allow_multiple_payments_per_invoice_id.png](assets/paypal_allow_multiple_payments_per_invoice_id.png)
1. Rulla längst ned och klicka **Spara**.

## Mer information

* [Blockera oavsiktliga betalningar](https://developer.paypal.com/docs/admin/setup-account/#block-accidental-payments) på PayPal Developer Docs.
* PayPal-betalningar i vår användarhandbok:
   * [PayPal Express-kassan](/docs/commerce-admin/stores-sales/payments/paypal/paypal-express-checkout.html)
   * [Andra PayPal-lösningar](/docs/commerce-admin/stores-sales/payments/paypal/paypal.html)
* I vår utvecklardokumentation:
   * [Ställ in PayPal-betalningsmetoder för Adobe Commerce i molninfrastruktur](/docs/commerce-cloud-service/user-guide/configure-store/paypal.html)
   * [Betalningsintegrering](https://developer.adobe.com/commerce/php/development/payments-integrations/)
