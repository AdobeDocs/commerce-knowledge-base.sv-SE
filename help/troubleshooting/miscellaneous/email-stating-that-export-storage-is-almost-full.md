---
title: "Skicka ett e-postmeddelande om att exportlagringen är nästan full"
description: Den här artikeln innehåller en lösning på problemet där du får ett e-postmeddelande om att exportlagringsutrymmet är nästan fullt.
feature: Cloud, Storage, Media
role: Developer
source-git-commit: 8f783cb4245911bded5e9946917e2f2c3e78a705
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# E-post som anger att exportlagringen är nästan full

Den här artikeln innehåller en lösning på problemet där du får ett e-postmeddelande om att exportlagringsutrymmet är nästan fullt.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur (alla versioner)

## Problem

Du får ett e-postmeddelande med följande innehåll men kan inte hitta *export* mapp:

*Vår övervakning har upptäckt att exportlagringsutrymmet i ditt kluster XXX är ca 85 % fullt.*
*Granska vid behov användningen, gör en rensning eller begär en uppgradering.*
*Observera också att vi försöker att automatiskt öka storleken när lagringen når tröskelvärdet för kritisk nivå.*

## Orsak

E-postmeddelandet avser **export** lagring, vilket är den mängd hårddisk som tilldelas filerna/mediet och inte en specifik mapp med namnet *export*.

## Lösning

Du bör granska filanvändningen i miljön. Kör det här kommandot för att få fram den befintliga användningen:

`df -h |grep data`

De typiska platserna där fillagringen troligen kommer att fyllas i är *pub/media/catalog/product/cache* eller *var/log* mappar. Kör det här kommandot med lämplig sökväg för att avgöra vilket diskutrymme som används av filerna */path/to/folder*:

`du -shc` */path/to/folder*

Om mediediskanvändningen utgör en stor del av det totala diskutrymmet kanske du bör aktivera [Snabb djupbildsoptimering](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization#deep-image-optimization)och sedan ta bort filerna i *pub/media/catalog/product/cache* mapp på servern manuellt.

## Relaterad läsning

[Kontrollera dedikerade kluster](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) i vår kunskapsbas för support.