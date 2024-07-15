---
title: Lagra bilder som inte visas efter distributionen
description: Den här artikeln innehåller en lösning för när bilder inte visas korrekt efter distributionen.
exl-id: 7e6bcebd-edff-437a-9103-2743443d2ed9
feature: Cache, Categories, Deploy, Storefront
role: Admin
source-git-commit: c4d586ca3980acbe4f33c5f2616ef7f3051bc7d3
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---

# Lagra bilder som inte visas efter distributionen

Den här artikeln innehåller en lösning för när bilder inte visas korrekt efter distributionen.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.2.x, 2.3.x

## Problem

När du använder ett storefront-tema med bildstorleksändring visas eller försvinner inte bilderna från katalogsidorna när de distribueras.

## Orsak

Detta kan bero på att bilderna läses in från cachen.

## Lösning

Om det inträffar kan du använda kommandot Magento för att återskapa bildcachen och visa bilderna på rätt sätt.

För att kunna utföra detta behöver du SSH-informationen och butiks-URL:en som är tillgängliga via [molnkonsolen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html).

1. SSH till ditt projekt som var en källa för [databasdumpen](/help/how-to/general/create-database-dump-on-cloud.md), vilket beskrivs i [SSH till miljön](https://devdocs.magento.com/guides/v2.3/cloud/env/environments-ssh.html#ssh) i vår utvecklardokumentation.
1. Återskapa bildcachen genom att köra:

   ```bash
   php bin/magento catalog:images:resize
   ```

1. Testa kategorisidorna via butikens URL.
