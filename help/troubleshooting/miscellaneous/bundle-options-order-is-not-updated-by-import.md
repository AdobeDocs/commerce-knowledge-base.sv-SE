---
title: Ordningen för paketalternativ uppdateras inte vid import
description: Den här artikeln innehåller en lösning på problemet när du har importerat produkter från en CSV-fil visas produktalternativen i en annan ordning än de visas i importfilen.
exl-id: 7f7bf782-4b35-4067-aa94-417097079f1f
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# Ordningen för paketalternativ uppdateras inte vid import

Den här artikeln innehåller en lösning på problemet när du har importerat produkter från en CSV-fil visas produktalternativen i en annan ordning än de visas i importfilen.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.2.x, 2.3.x
* Adobe Commerce lokal 2.2.x, 2.3.x
* Magento Open Source

## Problem

<u>Förutsättningar</u>:

Du har en giltig CSV-fil som innehåller paketprodukter.

<u>Steg som ska återskapas</u>:

1. Importera filen med [importfunktionen](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/import/data-import).
1. Öppna produktsidan för paketet.

<u>Förväntade resultat</u>:

Alternativordningen är densamma som i CSV-filen.

<u>Faktiska resultat</u>:

Alternativordningen skiljer sig från den i CSV-filen.

## Orsak

Alternativpositionen har inte deklarerats explicit.

## Lösning

1. Deklarera en position explicit för varje alternativ i parametern `position` i kolumnen `bundle_values` i CSV-filen. Mer information finns i [Redigera produktdata](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/examples/data-transfer-bundle-products#method-2-edit-the-product-data) i vår användarhandbok.
1. Upprepa importåtgärden.

Allmän information om import finns i [Importera paketprodukt](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/examples/data-transfer-bundle-products) i användarhandboken.
