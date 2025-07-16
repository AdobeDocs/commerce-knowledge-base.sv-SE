---
title: Ökad körningstid för asynkrona webbslutpunkter efter APSB25-08-säkerhetsuppdatering
description: Den här artikeln innehåller en snabbkorrigering för problemet där POST rest/all/async/bulk/V1/products begär in 1000+ poster får en avsevärt ökad körningstid efter att APSB25-08-säkerhetsuppdateringen har tillämpats.
feature: Security, Cache, REST, Products, Customers
role: Admin, Developer
exl-id: 784a48cb-1ef1-432b-b09f-ebcbb9bebf01
source-git-commit: f0c2e20e0bd6dab713be59c1c686ee2948445bd4
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Ökad körningstid för alla asynkrona webbslutpunkter efter APSB25-08-säkerhetsuppdatering

I den här artikeln finns en snabbkorrigering för alla asynkrona webbslutpunkter som `POST rest/all/async/bulk/V1/products` med över 1 000 poster som har betydligt längre körningstider efter att APSB25-08-säkerhetsuppdateringen har tillämpats.

## Berörda produkter och versioner

* Adobe Commerce (alla distributionsmetoder) 2.4.4, 2.4.4-p1, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p 10, 2.4.4-p11, 2.4.4-p12

* Adobe Commerce (alla distributionsmetoder) 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p 10, 2.4.5-p11

* Adobe Commerce (alla distributionsmetoder) 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8, 2.4.6-p9

* Adobe Commerce (alla distributionsmetoder) 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3, 2.4.7-p4

* Adobe Commerce (alla distributionsmetoder) 2.4.8

## Problem

När APSB25-08-säkerhetspatchen har tillämpats tar det betydligt längre tid att utföra `POST rest/all/async/bulk/V1/products`-begäranden med över 1 000 poster.

<u>Steg som ska återskapas</u>:

1. Gör en `POST rest/all/async/bulk/V1/products`-begäran med över 1 000 poster (namn, SKU och beskrivning räcker).
1. Observera hur lång tid det tar för begäran.
1. Använd APSB25-08-säkerhetsuppdateringen och rensa genererade data och cache med `se:di:co`.
1. Kör `bin/magento c:f`.
1. Gå till butiken för att säkerställa att cache och genererade filer finns på plats.
1. Upprepa begäran från steg 1.
1. Lägg märke till den ökade tiden för begäran.
1. Ta bort APSB25-08-säkerhetskorrigeringen, tömma cacheminnet, generera om koden och upprepa begäran från steg 1 för att bekräfta att körningstiden återgår till den normala. (Valfritt)

<u>Förväntade resultat</u>:

Körningstiden för `async/bulk`-begäranden har ökat avsevärt efter att säkerhetsuppdateringen har tillämpats.

<u>Faktiska resultat</u>:

Körningstiden för `async/bulk`-begäranden ska inte ha ökat avsevärt efter att säkerhetspatchen har tillämpats, även om en viss ökning av tiden förväntas.

## Lösning

Du löser problemet genom att använda [AC-14078-2-4x-comser-patch.zip](assets/AC-14078-2-4x-composer-patch.zip).

## Så här sätter du på plåstret

Zippa upp filen och se [Använda en kompositkorrigering från Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) i vår kunskapsbas för support för instruktioner.

## Relaterad läsning

* [Säkerhetsuppdatering för Adobe Commerce - APSB25-08](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27149)
