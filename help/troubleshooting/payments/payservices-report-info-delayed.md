---
title: Fördröjda betalningstjänster - rapportdata
description: I den här artikeln förklaras varför rapportering av data i Betalningstjänster kan fördröjas.
exl-id: 2f3249d1-be12-45bc-aa73-bef9766509ae
feature: Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Fördröjda betalningstjänster - rapportdata

I den här artikeln förklaras varför rapportering av data i Betalningstjänster kan fördröjas.

## Berörda produkter och versioner

* [Betalningstjänster](https://marketplace.magento.com/magento-payment-services.html) är nu kompatibelt med Adobe Commerce version 2.4.0 till 2.4.4.

## Problem

Rapporteringsdata för Betalningstjänster, för rapporter om betalningsstatus för Utbetalningar och Order, kan inte synkroniseras omedelbart.

När du har fakturerat (hämtat) en order eller utfärdat en kreditnota för en order, till exempel, kanske orderns status inte är omedelbart tillgänglig.

<u>Steg som ska återskapas</u>:

Krav: En beställning görs med funktionen Betalningstjänster.

1. En order är [fakturerad](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/invoices#create-an-invoice) (eller [annullerad](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order) eller [återbetald via kreditnota](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memos)) i [Admin](https://experienceleague.adobe.com/en/docs/commerce-admin/start/admin/admin).
1. Navigera till rapporten Orderbetalningsstatus för att se information om den ordern.
1. Statusen visas som `AUTHORIZED`, vilket är orderstatus före faktureringen eller annan orderåtgärd.

   Commerce har inte synkroniserat data och skickat dem till Payment Services, så den nya orderstatusen känns inte igen av rapporten än.

>[!NOTE]
>
>Detta är bara ett vanligt användningsfall. Det kan finnas andra användningsfall när en [orderåtgärd](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/orders#actions) inträffar och data inte är omedelbart tillgängliga i den tillämpliga rapporten.

<u>Förväntat resultat</u>:
Rapportdata fylls i omedelbart efter en åtgärd för en order.

<u>Faktiskt resultat</u>:
Det kan uppstå en fördröjning i synliga rapportdata för just slutförda orderåtgärder. Utbetalningsrapporter kan försenas med 24-48 timmar. Statusrapporter för orderbetalning kan ta några timmar.

## Orsak

Det finns två faktorer som påverkar fördröjningen av synliga data i Admin:

* Hur ofta du väljer att synkronisera (exportera och behålla) data från Commerce via [konfigurationen i Admin](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/configure-admin.html).
* Tidsram inom vilken PayPal publicerar rapportdata.

## Lösning

För statusrapporter för orderbetalning:

1. Navigera till **Försäljning** > **Betalningstjänster**.
1. Klicka på **Beställningsbetalningsstatus** om du vill visa rapporttabellen för orderbetalningsstatus.
1. Tvinga omsynkronisering genom att klicka på ikonen **framtvinga omsynkronisering** i det övre högra hörnet i rapporttabellen.
1. Du bör se den senaste uppdaterade tidsstämpeländringen och nya transaktioner som lästs in i rapporttabellen.

För PayPal-utbetalningsrapporter är det förväntade resultatet en fördröjning på 24-48 timmar på grund av beroendet av PayPals tidsram för datapublicering.
