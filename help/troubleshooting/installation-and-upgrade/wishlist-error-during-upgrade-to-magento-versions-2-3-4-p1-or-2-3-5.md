---
title: Önsklistefel vid uppgradering till Adobe Commerce version 2.3.4-p1 eller 2.3.5
description: I den här artikeln finns en fix för det kända problemet vid uppgradering till Adobe Commerce version 2.3.4-p1 och 2.3.5 som gäller ett önskelistefel under uppgraderingen till dessa versioner.
exl-id: 97479615-bf3f-4544-a9c1-8f19ba74318e
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Önsklistefel vid uppgradering till Adobe Commerce version 2.3.4-p1 eller 2.3.5

I den här artikeln finns en fix för det kända problemet vid uppgradering till Adobe Commerce version 2.3.4-p1 och 2.3.5 som gäller ett önskelistefel under uppgraderingen till dessa versioner.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.3.4-p1 och 2.3.5
* Adobe Commerce lokal 2.3.4-p1 och 2.3.5

## Problem

När du uppgraderar din Adobe Commerce (alla distributionsmetoder) och Magento Open Source till version 2.3.5 eller 2.3.4-p1 kan du få ett önskelistefel (som beskrivs nedan) från modulen:

```php
Magento_Wishlist
```

Om du uppgraderar från Adobe Commerce (alla distributionsmetoder)/Magneto Open Source version 2.3.4-p1 **till version 2.3.4-p2** eller från Adobe Commerce (alla distributionsmetoder)/Magneto Open Source version 2.3.5 **till version 2.3.5-p1** åtgärdas felet.

<u>Steg som ska återskapas</u>:

Uppgradera din Adobe Commerce (alla distributionsmetoder)/Magento Open Source till version 2.3.4-p1 eller 2.3.5.

<u>Förväntat resultat</u>:

Uppgraderingsprocessen till Adobe Commerce (alla distributionsmetoder)/Magento Open Source version 2.3.4-p1 eller 2.3.5 slutförs normalt.

<u>Faktiskt resultat</u>:

Under uppgraderingen visas följande fel:

```php
Module ‘Magento_Wishlist’:

Unable to apply data patch Magento\Wishlist\Setup\Patch\Data\CleanUpData for module Magento_Wishlist. Original exception message: Unable to unserialize value. Error: Syntax error
```

## Lösningar

* Om du uppgraderade till Adobe Commerce (alla distributionsmetoder)/Magneto Open Source version 2.3.5 **uppgraderar du till version 2.3.5-p1**. Adobe Commerce (alla distributionsmetoder)/Magento Open Source version 2.3.5-p1 ersätter 2.3.5.
* Om du uppgraderade till Adobe Commerce (alla distributionsmetoder)/Magento Open Source version 2.3.4-p1, **uppgradera till version 2.3.4-p2**. Adobe Commerce (all deployment methods)/Magneto Open Source version 2.3.4-p2 ersätter version 2.3.4-p1.

## Relaterad läsning

I vår utvecklardokumentation:

* [Adobe Commerce i molninfrastrukturguiden](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/overview)
* [Adobe Commerce i molninfrastruktur - uppgradera Adobe Commerce version](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)
* [Adobe Commerce lokalt och Magento Open Source - Uppgradera Adobe Commerce-programmet och -modulerna](https://experienceleague.adobe.com/sv/docs/commerce-operations/upgrade-guide/overview)
* [Konfiguration av önskelisteobjekt, sida](https://developer.adobe.com/commerce/frontend-core/guide/layouts/product-layouts/#wishlist-item-configure-page)
* [Moduler som tillhandahåller avancerad rapportering](https://developer.adobe.com/commerce/php/development/advanced-reporting/modules/)
