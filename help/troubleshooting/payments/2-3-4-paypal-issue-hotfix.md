---
title: 2.3.4 Säkerhetsuppdatering för PayPal
description: Den här artikeln innehåller en korrigering för fel som tas emot under orderplacering när du väljer en region i PayPal Express Checkout. Problemet orsakas av ändringar i Adobe Commerce version 2.3.4 och har att göra med hur adressfält för PayPal Express-utcheckning tolkas.
exl-id: 9f5ec100-49b0-4ac5-8951-32b5c4fe6bed
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 2.3.4 Säkerhetsuppdatering för PayPal

Den här artikeln innehåller en korrigering för fel som tas emot under orderplacering när du väljer en region i PayPal Express Checkout. Problemet orsakas av ändringar i Adobe Commerce version 2.3.4 och har att göra med hur adressfält för PayPal Express-utcheckning tolkas.

## Berörda versioner och produkter

* Adobe Commerce i molninfrastruktur v2.3.4
* Adobe Commerce lokalt v2.3.4

## Problem

Ett fel inträffar när du kommer in i landet och regionen under orderplaceringen i PayPal Express Checkout. Problemet kan reproduceras för alla länder där regionfältet i adressavsnittet är ett textfält (till skillnad från en nedrullningsbar meny).

<u>Steg som ska återskapas</u> :

1. Aktivera PayPal Express-utcheckning.
1. Lägg produkten i varukorgen som gäst eller när du är inloggad.
1. Gå till kassan.
1. Välj leveransadress. Till exempel *Storbritannien* . Ange sedan en inmatning i **Stat/provins** fält. Till exempel: *Nottinghamshire*.
1. Klicka på **Montera beställning** för att placera order. Du får en ordersida och ett mejl med orderbekräftelse.

<u>Förväntat resultat:</u>

Ordern har placerats ut.

<u>Faktiskt resultat:</u>

När du klickar på beställningsknappen visas ett fel:

```
Error 500: NOTICE: PHP message: PHP Fatal error: Uncaught Error: Call to a member
  function getId() on null in httpdocs/vendor/magento/module-paypal/Model/Api/Nvp.php:1527
```

## Lösning

För Adobe Commerce lokala handlare: Använd [snabbkorrigering,](https://magento.com/tech-resources/download#download2353) som finns i nedladdningsavsnittet på [magento.com](https://magento.com) portal i Mitt konto.

För Adobe Commerce på återförsäljare av molninfrastruktur: Adobe har tagit med korrigeringen i Cloud Patches for Commerce v1.0.2. Se [Cloud Patches for Commerce release notes](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html?itm_source=devdocs&amp;itm_medium=quick_search&amp;itm_campaign=federated_search&amp;itm_term=cloud%20patche) i utvecklardokumentationen för att hitta instruktioner om hur du använder det senaste paketet.

## Så här använder du patchen

Instruktioner finns i [Använda en kompositkorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.

## Relaterad läsning

* [Versionsinformation > Adobe Commerce 2.3.4 Versionsinformation > Tillämpa PayPal Express-utcheckningsproblemet med regionkorrigering för Adobe Commerce 2.3.4 för att åtgärda ett kritiskt problem med PayPal Express-utcheckning](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-4-commerce.html#apply-the-paypal-express-checkout-issue-with-region-patch-for-magento-234-to-address-a-critical-paypal-express-checkout-issue) i vår dokumentation för utvecklare.
