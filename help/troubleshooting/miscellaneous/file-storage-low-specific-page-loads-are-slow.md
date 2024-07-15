---
title: Låg fillagring, specifika sidinläsningar tar lång tid
description: Den här artikeln innehåller en lösning på problemet med brist på diskutrymme som orsakas av stora, avancerade bilder.
exl-id: 640c8f0d-f714-4cc1-a401-9264cfaf8e37
feature: Storage, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Låg fillagring, specifika sidinläsningar tar lång tid

Den här artikeln innehåller en lösning på problemet med brist på diskutrymme som orsakas av stora, avancerade bilder.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur, alla versioner som stöds
* Adobe Commerce lokala, alla versioner som stöds
* Magento Open Source, alla versioner som stöds

## Problem

Låg disklagring och långsam sidinläsning kan orsakas av stora, avancerade bilder som använder stora mängder lagringsutrymme i `pub/media/catalog/products` och delning av diskutrymme mellan mellanlagring och produktion (om inte en dedikerad mellanlagringsmiljö har etablerats).

## Orsak

Bilderna är inte optimerade för att balansera prestanda med visningskvalitet.

## Lösning

Innan du överför bilder bör du optimera och komprimera dem för att balansera prestanda med visningskvalitet. Detta bidrar till att öka utrymmet och minska sidinläsningstiden. PNG-filer ger mindre storlekar för bilder med stora enfärgade områden. JPEG ger mindre storlekar för allt annat. Använd den högsta komprimeringen (utan märkbar försämring). Detta är vanligtvis 60-80 procent.

Använd [Snabbt bildoptimering](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html) för att få mer lagringseffektiva bilder.

## Relaterad läsning

Mer information om hur du hanterar ditt diskutrymme (om du använder Adobe Commerce i molninfrastruktur) finns i [Hantera diskutrymme i Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) i Commerce on Cloud Infrastructure Guide.
