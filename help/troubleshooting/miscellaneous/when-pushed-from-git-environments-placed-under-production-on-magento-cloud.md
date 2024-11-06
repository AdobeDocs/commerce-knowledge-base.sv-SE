---
title: Nya miljöer som placerats under produktion när de trycks ned från Git
description: Den här artikeln innehåller en lösning på problemet med att nya miljöer placeras under produktionsmiljön i Adobe Commerce i molninfrastruktur när de flyttas från Git-versionskontrollsystemet.
exl-id: 279cd6d8-fd45-45ba-8456-8b397a01976f
feature: Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Nya miljöer som placerats under produktion när de trycks ned från Git

Den här artikeln innehåller en lösning på problemet med att nya miljöer placeras under produktionsmiljön i Adobe Commerce i molninfrastruktur när de flyttas från Git-versionskontrollsystemet.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen, [alla versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problem

<u>Förutsättningar</u>:

Ha en lokal Git-kontrollerad klon av projektet.

<u>Steg som ska återskapas</u>:

Du måste skapa en integrationsgren från mellanlagringsgrenen:

1. Växla till mellanlagringsgrenen genom att köra följande kommando i det lokala skalet: `git checkout staging`
1. Skapa en integreringsgren från mellanlagringsgrenen genom att köra följande kommando i det lokala skalet: `git checkout -b <branch>`
1. Skicka grenen till fjärrdatabasen och konfigurera en underordnad gren genom att köra följande kommando i det lokala gränssnittet: `git push --set-upstream origin <branch>`

<u>Förväntade resultat</u>:

Den nya grenen skapas under mellanlagringsgrenen.

<u>Faktiska resultat</u>:

Den nya grenen skapades under produktionsgrenen.

## Orsak

Det här är inte något fel. För att ställa in en överordnad gren för en annan gren bör handlaren använda magento-cloud CLI.

## Lösning

En överordnad gren kan bara anges efter att handlaren har aktiverat en nyligen skapad gren. Mer information finns i [Adobe Commerce om molninfrastruktur > Bitbucket-integrering](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/integrations/bitbucket#create-a-cloud-branch) i utvecklardokumentationen.

Om du vill uppdatera en överordnad för den befintliga grenen på servern använder du kommandot `magento-cloud environment:info` i magento-cloud CLI.

Exempel på användning:

`magento-cloud environment:info parent Staging`

Detta ställer in den överordnade grenen till &quot;Förproduktion&quot; för den utcheckade grenen.

## Relaterad läsning

* [Adobe Commerce i molninfrastruktur > magento-cloud CLI](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-overview) i vår utvecklardokumentation.
