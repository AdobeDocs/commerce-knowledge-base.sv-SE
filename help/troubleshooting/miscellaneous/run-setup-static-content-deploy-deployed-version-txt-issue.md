---
title: kör "setup:static-content:deploy" distribuerad_version.txt problem
description: Den här artikeln innehåller en korrigering för "deploy_version.txt" är inte skrivbart när kommandot "setup:static-content:deploy" körs manuellt.
exl-id: 88d8c126-349f-49cd-8f02-2a32e4994521
feature: Deploy, Page Content, SCD
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# kör `setup:static-content:deploy` distribuerad_version.txt-problem

Den här artikeln innehåller en korrigering för `deployed_version.txt` som inte är skrivbart när kommandot `setup:static-content:deploy` körs manuellt.

## Problem

Om du följer Adobe Commerce rekommendationer för molninfrastruktur för att använda [Configuration Management](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) (och flyttar genereringen av statiska resurser till byggfasen för att minska webbplatsens driftstopp under distributionen) kan du råka ut för följande fel när du kör kommandot `setup:static-content:deploy` manuellt:

```
{{cloud-project-id}}_stg@i:~$ php bin/magento setup:static-content:deploy
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/luma, Aheadworks/marketplace, Magento/backend
[Magento\Framework\Exception\FileSystemException]
The path "deployed_version.txt:///app/{{cloud-project-id}}_stg/pub/static/app/{{cloud-project-id}}_stg/pub/static/" is not writable
```

## Orsak

Vi har optimerat driftsättningsprocessen för att minska driftstoppen och har skapat länkar till statiska resursfiler i stället för att kopiera dem. Platsen där de statiska resurserna lagras är skrivskyddad, vilket är orsaken till att du får felmeddelandet ovan.

Vi rekommenderar starkt att du inte kör statiskt innehåll manuellt eftersom alla resurser redan har genererats och det inte finns någon skillnad mellan filerna om du gör det manuellt (temafilerna är skrivskyddade och du kan inte ändra dem), så det är ingen idé med en sådan åtgärd.

## Lösning

Om du fortfarande vill köra en statisk innehållsdistribution tar du bort symboler i katalogen `pub/static` och kör kommandot `setup:static-content:deploy` igen:

```
find pub/static/ -maxdepth 1 -type l -delete
```
