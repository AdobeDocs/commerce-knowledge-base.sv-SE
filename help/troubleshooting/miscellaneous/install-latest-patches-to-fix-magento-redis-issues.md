---
title: Installera de senaste patcharna för att åtgärda Adobe Commerce Redis-problem
description: Den här artikeln innehåller information om de senaste Redis-relaterade korrigeringsfilerna som finns i [Adobe Commerce on cloud infrastructure Patches](https://devdocs.magento.com/cloud/project/project-patch.html) package.
exl-id: 0335bc11-f679-4629-b4e7-6a0e68c3ae44
feature: Cache, Install, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Installera de senaste patcharna för att åtgärda Adobe Commerce Redis-problem

I den här artikeln finns information om de senaste Redis-relaterade korrigeringsfilerna som finns i [Adobe Commerce on cloud infrastructure Patches](https://devdocs.magento.com/cloud/project/project-patch.html) paket.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur 2.3.3, 2.3.4

## Problem

Extra processor- och minnesanvändning av Redis kan minska Adobe Commerce prestanda och därmed webbplatsens totala prestanda.

## Lösning

Använd de senaste patcharna från Adobe Commerce i molninfrastrukturspaketet. Detaljerade instruktioner finns i [Tillämpa patchar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

De senaste Redis-korrigeringsfilerna som levereras av Adobe Commerce om molninfrastrukturkorrigeringspaketet bidrar till följande:

* minska storleken på nätverkskommunikation för Redis
* åtgärda konkurrensförhållanden som leder till extra minnesförbrukning
* ändra cachekortet så att det täcker vräkningsfall
* minska Redis CPU-förbrukning

Adobe Commerce rekommenderar även uppgradering till Redis 5 om du kör Adobe Commerce i molninfrastruktur 2.3.3 eller senare.
