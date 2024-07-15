---
title: 'Distributionsfel: SQLSTATE[HY000]'
description: Den här artikeln innehåller en lösning på problemet där distributionen misslyckas på grund av SQLSTATE[HY000]-felet.
exl-id: c6da6275-9327-4a5c-99ed-93a53952ba42
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---

# Distributionsfel: SQLSTATE[HY000]

Den här artikeln innehåller en lösning på problemet där distributionen misslyckas på grund av SQLSTATE[HY000] -felet.

## Berörda produkter och versioner

* Adobe Commerce, [alla distributionsmetoder](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Ett SQLSTATE-fel inträffar under distributionen.

```sql
Updating modules:
SQLSTATE[HY000]: General error: 23 Out of resources when opening file '/tmp/#sql_565c_0.MAD' (Errcode: 24 "Too many open files"),
```

## Orsak

Kron körs under distributionen.

## Lösning

Lös problemet genom att stoppa cron från att köras genom att öppna kommandoraden och köra följande kommando:
`./vendor/bin/ece-tools cron:disable`.
