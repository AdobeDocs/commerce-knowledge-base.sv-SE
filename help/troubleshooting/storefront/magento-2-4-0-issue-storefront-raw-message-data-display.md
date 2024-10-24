---
title: "Adobe Commerce 2.4.0 issue: storefront raw message data display"
description: Den här artikeln innehåller en lösning på problemet när alla felmeddelanden på butiken visas med plustecknet (+) i stället för ett mellanslag. Den här lösningen hjälper felmeddelanden att förbli läsbara.
exl-id: f44fe434-a320-4e7e-a876-9575921749f3
feature: Storefront
role: Admin
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# Adobe Commerce 2.4.0-utgåva: visning av råa meddelanden i butiker

Den här artikeln innehåller en lösning på problemet när alla felmeddelanden på butiken visas med plustecknet (+) i stället för ett mellanslag. Den här lösningen hjälper felmeddelanden att förbli läsbara.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.4.0
* Adobe Commerce lokal 2.4.0.

## Problem

<u>Steg att återskapa:</u>

1. Gå till sidan **Skapa nytt konto** i butiken.
1. Skapa ett nytt konto med en registrerad e-postadress. Följande meddelande visas:

`There+is+already+an+account+with+this+email+address.+If+you+are+sure+that+it+is+your+email+address,+click+here+to+get+your+password+and+access+your+account.`

## Orsak

Problemet orsakas av ett PHP 7.4.2-problem som rör set\\read cookies. Se [PHP BUG \#79174 setcookie() kodar blanksteg som \`+\`, men $\_COOKIE avkodar dem inte längre](https://bugs.php.net/bug.php?id=79174).

## Lösning

Använd en annan version av PHP 7.4.x för att lösa problemet. PHP 7.4.2 stöds inte av Adobe Commerce 2.4.0.

## Relaterade läsningar i vår kunskapsbas:

* [Commerce 2.4.0: Braintree betalningsmetoder visas inte i kassan för flera adresser](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0: Uppdatering av kundens aktiviteter fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0: Exportavgifter fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0: Knappen &quot;Lägg till markeringar i kundvagnen&quot; fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
