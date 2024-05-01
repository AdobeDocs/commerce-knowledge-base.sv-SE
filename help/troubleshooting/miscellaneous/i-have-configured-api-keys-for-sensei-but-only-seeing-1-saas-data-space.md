---
title: Jag har konfigurerat API-nycklar för Sensei men bara ser ett SaaS-datautrymme
description: Den här artikeln innehåller en lösning på de problem där du bara ser ett SaaS-datautrymme när du har konfigurerat API-nycklarna för Sensei.
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Jag har konfigurerat API-nycklar för Sensei men bara ser ett SaaS-datautrymme

Den här artikeln innehåller en lösning på de problem där du bara ser ett SaaS-datautrymme när du har konfigurerat API-nycklarna för Sensei.

## Berörda produkter och versioner

* Adobe Commerce (alla distributionsmetoder): alla versioner
* Magento Open Source: alla versioner
* Tillägg eller teknik (snabbt, New Relic osv.), Adobe Sensei (Recommendations/Live Search)

## Problem

Jag har konfigurerat API-nycklarna för Sensei, men jag ser bara ett SaaS-datautrymme.

## Orsak

Hur många SaaS-datamallar som visas beror på din Commerce-licens:

* Adobe Commerce - ett produktionsdatautrymme; två testdatautrymme
* Magento Open Source - Ett produktionsdatautrymme utan testdatautrymme

## Lösning

* Kontrollera att API-nycklarna har skapats på kontoägarens konto. Även om du har fått delad åtkomst till deras konto och skapat nycklarna för ditt konto, ger detta dig inte mer än ett dataminne.
* Om nycklarna har genererats på kontoägarens konto kontrollerar du att licensen är aktiv, dvs. att det inte finns några väntande fakturor.
