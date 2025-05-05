---
title: Installera de senaste patcharna för att åtgärda Adobe Commerce Redis-problem
description: Den här artikeln innehåller information om de senaste Redis-relaterade korrigeringsfilerna som finns i [Adobe Commerce on cloud infrastructure Patches](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) package.
exl-id: 0335bc11-f679-4629-b4e7-6a0e68c3ae44
feature: Cache, Install, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Installera de senaste patcharna för att åtgärda Adobe Commerce Redis-problem

I den här artikeln finns information om de senaste Redis-relaterade korrigeringsfilerna som finns i [Adobe Commerce för molninfrastrukturkorrigeringsfiler](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) .

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur 2.3.3, 2.3.4

## Problem

Extra processor- och minnesanvändning av Redis kan minska Adobe Commerce prestanda och därmed webbplatsens totala prestanda.

## Lösning

Använd de senaste patcharna från Adobe Commerce i molninfrastrukturspaketet. Mer information finns i [Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i utvecklardokumentationen.

De senaste Redis-korrigeringsfilerna som levereras av Adobe Commerce om molninfrastrukturkorrigeringspaketet bidrar till följande:

* minska storleken på nätverkskommunikation för Redis
* åtgärda konkurrensförhållanden som leder till extra minnesförbrukning
* ändra cachekortet så att det täcker vräkningsfall
* minska Redis CPU-förbrukning

Adobe Commerce rekommenderar även uppgradering till Redis 5 om du kör Adobe Commerce i molninfrastruktur 2.3.3 eller senare.
