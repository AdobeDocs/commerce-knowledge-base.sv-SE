---
title: Önsklistefel vid uppgradering till Adobe Commerce version 2.3.4-p1 eller 2.3.5
description: I den här artikeln finns en fix för det kända problemet vid uppgradering till Adobe Commerce version 2.3.4-p1 och 2.3.5 som gäller ett önskelistefel under uppgraderingen till dessa versioner.
exl-id: 97479615-bf3f-4544-a9c1-8f19ba74318e
feature: Install, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
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

Uppgradera från Adobe Commerce (alla distributionsmetoder)/Magneto Open Source version 2.3.4-p1 **till version 2.3.4-p2** eller från Adobe Commerce (alla distributionsmetoder)/Magneto Open Source version 2.3.5 **till version 2.3.5-p1** åtgärdar felet.

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

* Om du uppgraderade till Adobe Commerce (alla distributionsmetoder)/Magneto Open Source version 2.3.5, **uppgradera till version 2.3.5-p1**. Adobe Commerce (alla distributionsmetoder)/Magento Open Source version 2.3.5-p1 ersätter 2.3.5.
* Om du uppgraderade till Adobe Commerce (alla distributionsmetoder)/Magento Open Source version 2.3.4-p1, **uppgradera till version 2.3.4-p2**. Adobe Commerce (alla distributionsmetoder)/Magneto Open Source version 2.3.4-p2 ersätter version 2.3.4-p1.

## Relaterad läsning

I vår utvecklardokumentation:

* [Adobe Commerce i molninfrastrukturguide](https://devdocs.magento.com/cloud/bk-cloud.html)
* [Adobe Commerce i molninfrastruktur - uppgradera Adobe Commerce version](https://devdocs.magento.com/cloud/project/project-upgrade.html)
* [Adobe Commerce lokal och Magento Open Source - uppgradera Adobe Commerce program och moduler](https://devdocs.magento.com/guides/v2.3/comp-mgr/bk-compman-upgrade-guide.html)
* [Sida för konfiguration av önskelisteobjekt](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/layouts/product-layouts.html#wishlist-item-configure-page)
* [Moduler som ger avancerad rapportering](https://devdocs.magento.com/guides/v2.3/advanced-reporting/modules.html)
