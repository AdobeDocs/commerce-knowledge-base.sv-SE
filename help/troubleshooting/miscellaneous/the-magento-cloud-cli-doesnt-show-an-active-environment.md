---
title: '"Magento-cloud" [!DNL CLI] visar ingen aktiv miljö'
description: I den här artikeln beskrivs ett känt Adobe Commerce-problem där "Magento-cloud" [!DNL CLI] (kommandoradsverktyget) visar inte någon aktiv miljö.
feature: Cloud, Integration, Configuration
role: Developer
exl-id: 3c1b5de2-8888-4531-9dc1-cd478e3c96fc
source-git-commit: 5eac8bb54e205eff6a96e279295cd12db1009f0a
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 0%

---

# The `Magento-cloud` [!DNL CLI] visar ingen aktiv miljö

## Problem

Det finns flera aktiva miljöer, och du försöker interagera med en miljö genom att köra en `Magento-cloud` [!DNL CLI] (kommandoradsverktyg). (Till exempel: `ssh`, `db:size`, `db:sql`, osv.)
Uppmaningen att välja önskad miljö listar dock inte den här miljön. (Exempel: integreringsmiljön)

```
Enter a number to choose an environment:
Default: master
  [0] integration2 (type: development)
  [1] master (type: development)
  [2] production
  [3] staging
 >
```

## Orsak

Miljön kanske inte är tillgänglig på grund av en pågående, fastsatt eller misslyckad distribution.

## Lösning

Du måste ange miljön manuellt med `e|-environment` flagga.

1. Hitta en lista över aktiva miljöer och notera miljönamnen:

```
$ magento-cloud environment: list |grep "Active\|ID"
Your environments are:

| ID                     | Title            | Status       | Type           |
| Master                 | Master           | Active       | Development    |
|   Production           | Production       | Active       | Production     |
|     Staging            | Staging          | Active       | Staging        |
|       Integration      | Integration      | Active       | Development    |
|          Integration 2 | Integration 2    | Active       | Development    |
```

2. Ange miljöns ID med ditt kommando:

`magento-cloud ssh -e integration`
