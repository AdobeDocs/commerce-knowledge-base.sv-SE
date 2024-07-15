---
title: Problem med att skapa etiketter i Adobe Commerce 2.4.0
description: I den här artikeln finns en patch för ett känt Adobe Commerce 2.4.0-problem där det inte går att skapa någon fraktsetikett.
exl-id: 722689d9-0c90-4a9d-8449-e93c6585b7c3
feature: Orders, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Problem med att skapa etiketter i Adobe Commerce 2.4.0

I den här artikeln finns en patch för ett känt Adobe Commerce 2.4.0-problem där det inte går att skapa någon fraktsetikett.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.4.0
* Adobe Commerce om molninfrastruktur 2.4.0

## Problem

<u>Förutsättningar</u>: skapa en order med leveransmetoden FedEx, DHL, UPS eller USPS.

### Scenario 1: Skapa en etikett när du lägger till en leverans

<u>Steg att återskapa:</u>

1. Öppna den placerade ordern i Admin, under **Försäljning** > **Beställningar**.
1. Klicka på knappen **Leverera**. Sidan **Ny leverans** öppnas.

<u>Förväntat resultat:</u>

Kryssrutan **Skapa leveransetikett** visas längst ned på sidan.

<u>Faktiskt resultat:</u>

Kryssrutan **Skapa leveransetikett** visas inte.

### Scenario 2: Skapa en etikett för befintlig leverans

<u>Steg att återskapa:</u>

1. Öppna den placerade ordern i Admin, under **Försäljning** > **Beställningar**.
1. Klicka på knappen **Leverera**. Sidan **Ny leverans** öppnas.
1. Klicka på knappen **Skicka leverans**. En leverans skapas.
1. Öppna den nyligen skapade leveransen.
1. Klicka på knappen **Skapa leveransetikett** . Dialogrutan **Skapa paket** öppnas.

<u>Förväntat resultat:</u>

Knappen **Lägg till produkter i paket** i det modala fönstret **Skapa paket** visar fält med orderobjekt.

<u>Faktiskt resultat:</u>

Det modala fönstret **Skapa paket** visas inte korrekt. Det går inte att lägga till orderobjekt i leveransen.

## Lösning

Använd den patch som finns i den här artikeln.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[MC-35514-2.4.0-CE-composiser-2.patch](assets/MC-35514-2.4.0-CE-composer-2.patch.zip)

Korrigeringen kan också laddas ned både `.git` och `.composer` på sidan [Adobe Commerce Downloads](https://magento.com/tech-resources/download) under **Patchar** i den vänstra kolumnnavigeringen. Sök efter MC-35514-korrigering.

### Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce on cloud infrastructure version 2.4.0
* Adobe Commerce lokal version 2.4.0

## Så här sätter du på plåstret

Mer information finns i [Använda en dispositionsruta från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## Bifogade filer
