---
title: Advanced Reporting 404 error on split database solution
description: Den här artikeln innehåller en patch för användare av Adobe Commerce 2.3.x med [split database solution](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master) som får ett 404-fel när de försöker använda Advanced Reporting.
exl-id: b81d4ada-5f38-4882-bc5b-ab4ccd63fc5f
feature: Commerce Intelligence
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Advanced Reporting 404 error on split database solution

Den här artikeln innehåller en patch för Adobe Commerce 2.3.x-användare med den [delade databaslösningen](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master) som får ett 404-fel när de försöker använda Advanced Reporting.

## Berörda produkter och versioner

Adobe Commerce 2.3.0 - 2.3.5-p1

## Problem

Korrigeringen åtgärdar ett problem där fel anslutningsnamn används för att samla in offertdata. På grund av fel anslutningsnamn skickas inte offertdata till Magento Businessen Intelligence (MBI) och rapporterna kan inte genereras.

## Lösning

Använd den [korrigering](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip) som anges i den här artikeln.

## Lappa

Korrigeringen är kopplad till den här artikeln. Klicka på följande länk om du vill hämta den:

[MDVA-26831\_EE\_2.3.4\_v1.composer.patch](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip)

## Så här sätter du på plåstret

Zippa upp filen och följ instruktionerna i [Använda en kompositkorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).
