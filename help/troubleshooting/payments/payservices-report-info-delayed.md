---
title: Fördröjda betalningstjänster - rapportdata
description: I den här artikeln förklaras varför rapportering av data i Betalningstjänster kan fördröjas.
exl-id: 2f3249d1-be12-45bc-aa73-bef9766509ae
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
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

1. En order är [fakturerad](https://docs.magento.com/user-guide/sales/invoice-create.html) (eller [avbruten](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order) eller [återbetalas via kreditnota](https://docs.magento.com/user-guide/sales/credit-memos.html)) i [Administratör](https://docs.magento.com/user-guide/stores/admin.html).
1. Navigera till rapporten Orderbetalningsstatus för att se information om den ordern.
1. Statusen visas som `AUTHORIZED`, som är orderstatus före fakturering eller annan orderåtgärd.

   Commerce har inte synkroniserat data och skickat dem till Payment Services, så den nya orderstatusen känns inte igen av rapporten än.

>[!NOTE]
>
>Detta är bara ett vanligt användningsfall. Det kan finnas andra användningsområden när [orderåtgärd](https://docs.magento.com/user-guide/sales/order-actions.html) inträffar och uppgifterna inte är omedelbart tillgängliga i den tillämpliga rapporten.

<u>Förväntat resultat</u>: Rapportdata fylls i omedelbart efter en åtgärd för en order.

<u>Faktiskt resultat</u>: Det kan uppstå en fördröjning i synliga rapportdata för just slutförda orderåtgärder. Utbetalningsrapporter kan försenas med 24-48 timmar. Statusrapporter för orderbetalning kan ta några timmar.

## Orsak

Det finns två faktorer som påverkar fördröjningen av synliga data i Admin:

* Hur ofta du väljer att synkronisera (exportera och behålla) data från Commerce via [konfiguration i administratören](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/configure-admin.html).
* Tidsram inom vilken PayPal publicerar rapportdata.

## Lösning

För statusrapporter för orderbetalning:

1. Navigera till **Försäljning** > **Betalningstjänster**.
1. Klicka **Status för orderbetalning** om du vill visa rapportregister för orderbetalningsstatus.
1. Tvinga omsynkronisering genom att klicka på **tvinga omsynkronisering** i det övre högra hörnet i rapporttabellen.
1. Du bör se den senaste uppdaterade tidsstämpeländringen och nya transaktioner som lästs in i rapporttabellen.

För PayPal-utbetalningsrapporter är det förväntade resultatet en fördröjning på 24-48 timmar på grund av beroendet av PayPals tidsram för datapublicering.
