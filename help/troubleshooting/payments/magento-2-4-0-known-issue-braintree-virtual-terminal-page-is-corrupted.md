---
title: Adobe Commerce 2.4.0 Braintree Virtual Terminal-sidan är skadad
description: Den här artikeln innehåller en patch för det kända Adobe Commerce 2.4.0-problemet, där Braintree Virtual Terminal-sidan inte läser in rätt gränssnittselement eller ett felmeddelande om Braintree inte är konfigurerat.
exl-id: 1d4d762d-2ab3-4752-ad6d-1eb6a179917d
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 Braintree Virtual Terminal-sidan är skadad

Den här artikeln innehåller en patch för det kända Adobe Commerce 2.4.0-problemet, där Braintree Virtual Terminal-sidan inte läser in rätt gränssnittselement eller ett felmeddelande om Braintree inte är konfigurerat.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.4.0
* Adobe Commerce om molninfrastruktur 2.4.0

## Problem

### Scenario 1: Betalningsmetoden Braintree har konfigurerats

<u>Steg som ska återskapas:</u>

Gå till Commerce Admin **Försäljning** > **Virtuell terminal för Braintree** . ** **

<u>Förväntat resultat:</u>

The **Virtuell terminal för Braintree** sidan läses in med rätt användargränssnitt.

<u>Faktiskt resultat:</u>

Användargränssnittet för **Virtuell terminal för Braintree** sidan är skadad.

### Scenario 2: Betalningsmetoden Braintree har konfigurerats

<u>Steg som ska återskapas:</u>

Gå till Commerce Admin **Försäljning** > **Virtuell terminal för Braintree** . ** **

<u>Förväntat resultat:</u>

The **Virtuell terminal för Braintree** sidan läses in med rätt användargränssnitt och en varning visas som talar om att Braintree inte har konfigurerats än.

<u>Faktiskt resultat:</u>

Användargränssnittet för **Virtuell terminal för Braintree** sidan är skadad och ingen varning visas.

## Lösning

Använd den patch som finns i den här artikeln.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[BUNDLE-2670-composer.patch](assets/BUNDLE-2670-composer.patch.zip)

### Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce om molninfrastruktur 2.4.0
* Adobe Commerce lokal 2.4.0

## Så här sätter du på plåstret

Se [Använda en kompositkorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) för instruktioner.

## Bifogade filer
