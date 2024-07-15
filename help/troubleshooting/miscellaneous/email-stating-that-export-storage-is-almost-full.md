---
title: E-post som anger att exportlagringen är nästan full
description: Den här artikeln innehåller en lösning på problemet där du får ett e-postmeddelande om att exportlagringsutrymmet är nästan fullt.
feature: Cloud, Storage, Media
role: Developer
exl-id: 7dae295c-919c-46c5-bf63-7d3467c2e07f
source-git-commit: 89f985b832545f1fbccf94aac1d60f1e767b5bc4
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# E-post som anger att exportlagringen är nästan full

Den här artikeln innehåller en lösning på problemet där du får ett e-postmeddelande om att exportlagringsutrymmet är nästan fullt.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur (alla versioner)

## Problem

Du får ett e-postmeddelande med följande innehåll men kan inte hitta mappen *exporting*:

*Vår övervakning har upptäckt att exportlagringsutrymmet i ditt kluster XXX är ca 85 % fullt.*
*Granska vid behov användningen, gör en rensning eller begär en uppgradering.*
*Observera också att vi automatiskt försöker göra en uppstorleksändring när lagringen når tröskelvärdet för kritisk nivå.*

## Orsak

E-postmeddelandet refererar till lagringsutrymmet **exporting**, som är den mängd disk som tilldelats filerna/mediet, och inte till en specifik mapp med namnet *exporting*.

## Lösning

Du bör granska filanvändningen i miljön. Kör det här kommandot för att få fram den befintliga användningen:

`df -h |grep data`

De typiska platserna där fillagringen troligen kommer att fyllas i är mapparna *pub/media/catalog/product/cache* eller *var/log*. Om du vill ta reda på vilket diskutrymme som används av filerna kör du det här kommandot med rätt sökväg */sökväg/till/mapp*:

`du -shc` */path/to/folder*

Om mediediskanvändningen utgör en stor del av det totala diskutrymmet kanske du vill aktivera [Optimering av djup](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization#deep-image-optimization) och sedan ta bort filerna i mappen *pub/media/catalog/product/cache* på servern manuellt.

## Relaterad läsning

[Kontrollera dedikerade kluster](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) i vår kunskapsbas för support.
