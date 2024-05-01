---
title: Felsökning av PayPal på Adobe Commerce
description: Den här artikeln innehåller lösningar på problem med att bearbeta betalningar via PayPal, särskilt PayFlow Pro-lösningen. Vissa rekommendationer i den här artikeln kan verka självklara. Vi ber dig att prova de felsökningsalternativ som listas i den här kunskapsbasen och inkludera all information i de biljetter du anger. Adobe Commerce eller PayPal Support Engineers kommer att be dig utföra dessa steg när du diagnostiserar dina problem.
exl-id: f0772515-8456-4f08-84b4-aeef44516f2a
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# Felsökning av PayPal på Adobe Commerce

Den här artikeln innehåller lösningar på problem med att bearbeta betalningar via PayPal, särskilt PayFlow Pro-lösningen. Vissa rekommendationer i den här artikeln kan verka självklara. Vi ber dig att prova de felsökningsalternativ som listas i den här kunskapsbasen och inkludera all information i de biljetter du anger. Adobe Commerce eller PayPal Support Engineers kommer att be dig utföra dessa steg när du diagnostiserar dina problem.

## Vanliga problem

De flesta problem med PayPal-betalningar har liknande symtom: när du har angett betalningsinformation och går vidare till kassan behandlas inte betalningen. Det kan i stället finnas ett felmeddelande, en misslyckad betalningsprocess eller en tom sida.

## Verifiera dina inloggningsuppgifter, krypteringsnycklar och licenser

Möjliga problem: feltryck i kontoinformationen (användarnamn, lösenord), ogiltiga konton, utgångna eller ospecificerade licenser, ogiltiga offentliga och personliga nycklar och många andra aspekter. Om du vill hitta de problemen kan du behöva kontrollera dina inställningar för betalningskonfiguration.

## Använd konsekventa inställningar i Adobe Commerce och PayPal

Se till att du har använt samma inställningar och aktiverat samma funktioner i kontoinställningarna för Commerce Admin och PayPal.

### Exempel på inställningsproblem

När du använder lösningen PayPal Express Checkout måste transaktioner som baseras på AVS/CSC-svar avvisas i **PayPal Manager** (Tjänstinställningar > Konfigurera > Säkerhetsalternativ) och i **Commerce Admin** ( **Lager** > Konfiguration > **Försäljning** > **Betalningsmetoder** ...).
![magento_paypal_settings_2.4.1.png](assets/magento_paypal_settings_2.4.1.png)
Mer information finns i dokumentationen: [PayPal](https://www.paypalobjects.com/en_US/vhelp/paypalmanager_help/setup.htm) och [Adobe Commerce](/docs/commerce-admin/stores-sales/payments/paypal/paypal-express-checkout.html) i vår användarhandbok.

## Tillåt referenstransaktioner

Om betalningsmetoden PayPal innefattar API med faktureringsavtal och referenstransaktioner måste du se till att de är aktiverade och konfigurerade korrekt i inställningarna.

### Ytterligare felsökning

Se följande artiklar:

* [PayPal-gateway avvisade begäran - dubblettfakturautleverans](/help/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.md) i vår kunskapsbas för support.
* [Ändra öknings-ID för ny lagringsenhet](/help/how-to/general/change-increment-id-for-a-db-entity-order-invoice-credit-memo-etc-on-particular-store.md) i vår kunskapsbas för support.

## Kontakta supporten för att samla in avancerade betalningsloggar

Om du vill felsöka komplicerade betalningsproblem kan Adobe Commerce supportteam be dig att använda en dedikerad korrigeringsfil för att aktivera avancerad betalningsloggning. I det här fallet bör du göra följande:

[Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) med följande uppgifter:

* Ange ditt problem med så många detaljer som möjligt.
* Visa en lista över de steg du försökte utföra från den här artikeln, kunskapsbasen och andra resurser. Inkludera alla resultat.
* Begär en patch för avancerad betalningsloggning (referensnummer MDVA-4352) och instruktioner för hur korrigeringen ska användas.

Om du får korrigeringsfilen för avancerad betalningsloggning:

* Lägg på plåstret.
* Samla in loggar och bifoga dem till [supportbiljett](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
* Vänta på ytterligare rekommendationer från Adobe Commerce Support Team.
