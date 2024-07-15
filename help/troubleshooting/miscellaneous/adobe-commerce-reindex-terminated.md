---
title: '"Adobe Commerce cloud: reindex avslutas med meddelandet "Killed"'
description: '* Adobe Commerce on cloud infrastructure (all versions)'
exl-id: 36ed9c9f-8280-41db-9df3-fe842dade4b1
feature: Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Adobe Commerce-moln: omindexering avslutas med meddelandet `Killed`

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur (alla versioner)

## Problem

Du försöker köra en omindexering på integreringsgrenen (eller på mellanlagring för startarkitekturprojektet) och processen avslutas med meddelandet `Killed`.

## Orsak

Detta beror vanligtvis på att PHP-processerna börjar få slut på minne.
Den vanligaste orsaken till detta är ett stort antal produkter, butiker och/eller kundgrupper på instansen.

## Lösning

1. Minska antalet produkter (samt kundgrupper och butiker - om tillämpligt).
1. Begränsa användningen till en eller två samtidiga användare.
1. Inaktivera cron-jobb och kör manuellt efter behov.
1. Om detta inte har gjorts tidigare, begär du en uppgradering till Enhanced Integration-miljöerna - notera begränsningen av antalet miljöer som du begränsas till när uppgraderingen har utförts. Mer information finns i artikeln [Förbättrad integreringsmiljö - Pro och Starter](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) i vår kunskapsbas för support.

## Relaterad läsning:

I vår utvecklardokumentation:

* [Pro-arkitektur > Integreringsmiljö](https://devdocs.magento.com/cloud/architecture/pro-architecture.html#cloud-arch-int)
* [Startarkitektur > Mellanlagringsmiljö](https://devdocs.magento.com/cloud/architecture/starter-architecture.html#cloud-arch-stage)
