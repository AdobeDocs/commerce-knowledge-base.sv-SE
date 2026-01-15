---
title: 'Adobe Commerce 2.4.0: undantag under installationen av B2B 1.2.0'
description: I den här artikeln finns en korrigering för ett känt Adobe Commerce-fel för ett undantag som inträffar under "setup:upgrade" vid installation av B2B 1.2.0.
exl-id: 2c1dadd9-7754-4b4c-8d37-b75c13beae5c
feature: B2B, Install, Upgrade
role: Developer
source-git-commit: 05297c82b292b8ccc88018c58e991bd3a32d6ffa
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: undantag under installationen av B2B 1.2.0

I den här artikeln finns en korrigering för ett känt Adobe Commerce-problem för ett undantag som inträffar under `setup:upgrade` vid installation av B2B 1.2.0.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.4.0
* Adobe Commerce om molninfrastruktur 2.4.0
* B2B 1.2.0

## Problem

<u>Steg som ska återskapas</u>

1. Installera Adobe Commerce med fler än en butik skapad.
1. Skapa ytterligare en butik.
1. Installera B2B 1.2.0.

>[!WARNING]
>
>Uppgraderingen av B2B-instanser med fler än 1 butik från en version under 1.2.0 eller Commerce under 2.4.0 påverkas också.

<u>Förväntat resultat</u>

Installation av B2B 1.2.0.

<u>Faktiskt resultat</u>

När `setup:upgrade` kör installationen av B2B 1.2.0 visas det här felet i modulen `PurchaseOrder`:

```php
Module 'Magento_PurchaseOrder':
  Unable to apply data patch Magento\PurchaseOrder\Setup\Patch\Data\InitPurchaseOrderSalesSequence
  for module Magento_PurchaseOrder. Original exception message: DDL statements
  are not allowed in transactions
```

## Lösning

Använd den patch som finns i den här artikeln.

## Lappa

Korrigeringen är kopplad till den här artikeln och kan hämtas i både `.composer`- och `.git`-format (när du har packat upp filerna).

Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet, eller klickar på någon av följande länkar:

* [Dispositionsruta B2B-716\_disposition.patch](assets/B2B-716_composer.patch.zip)
* [Git patch B2B-716\_git.patch](assets/B2B-716_git.patch.zip)

## Så här lägger du på en patch

<u>Kompositionsruta </u>

Mer information finns i [Använda en dispositionskorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

<u>Git-korrigering </u>

* Se [Tillämpa korrigeringsfiler](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i utvecklardokumentationen för Git-korrigeringsanvisningar för Adobe Commerce i molninfrastrukturen.
* Se [Använda korrigeringsfiler: Anpassade korrigeringsfiler](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview#custom-patches) i utvecklardokumentationen för Git-korrigeringsanvisningar för Adobe Commerce.

## Relaterad läsning

* [Adobe Commerce 2.4.0: Braintree betalningsmetoder visas inte i kassan för flera adresser](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problem med Adobe Commerce 2.4.0: Felmeddelande vid val av lokal betalningsmetod för vissa länder vid utcheckning](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0 B2B Admin kan inte lägga till en konfigurerbar produkt att citera](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
