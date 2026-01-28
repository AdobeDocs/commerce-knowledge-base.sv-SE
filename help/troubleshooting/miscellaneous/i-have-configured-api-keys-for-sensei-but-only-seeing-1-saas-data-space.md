---
title: Jag har konfigurerat API-nycklar för Adobe AI men bara ser ett SaaS-datautrymme
description: Den här artikeln innehåller en lösning på de problem där du bara ser ett SaaS-dataområde efter att du har konfigurerat API-nycklarna för Adobe AI.
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
source-git-commit: 27b0836380c3040b26076b9cb81b9328cb2c9ff2
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Jag har konfigurerat API-nycklar för Adobe AI men bara ser ett SaaS-datautrymme

Den här artikeln innehåller en lösning på de problem där du bara ser ett SaaS-dataområde efter att du har konfigurerat API-nycklarna för Adobe AI.

## Berörda produkter och versioner

* Adobe Commerce (alla distributionsmetoder): alla versioner
* Magento Open Source: alla versioner
* Tillägg eller teknik (snabbt, New Relic osv.), Adobe AI (produktrekommendationer/Live Search)

## Problem

Jag har konfigurerat API-nycklarna för Adobe AI, men jag ser bara ett SaaS-datautrymme.

## Orsak

Hur många SaaS-datamallar som visas beror på din Commerce-licens:

* Adobe Commerce - ett produktionsdatautrymme; två testdatautrymme
* Magento Open Source - ett produktionsdatautrymme; inga testdatautrymme

## Lösning

* Kontrollera att API-nycklarna har skapats på kontoägarens konto. Även om du har fått delad åtkomst till deras konto och skapat nycklarna för ditt konto, ger detta dig inte mer än ett dataminne.
* Om nycklarna har genererats på kontoägarens konto kontrollerar du att licensen är aktiv, dvs. att det inte finns några väntande fakturor.
