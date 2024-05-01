---
title: Ordna om molngrenar i Adobe Commerce
description: I den här artikeln beskrivs hur du kan ordna om molngrenar på Adobe Commerce, om de inte är ordnade enligt rätt hierarki. Om du inte har grenarna ordnade i rätt hierarki kommer du inte att kunna sammanfoga till rätt överordnad gren - den kommer att gå till den befintliga överordnade grenen.
exl-id: 4fc0de96-da66-4634-a38a-6a1536855f8f
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Ordna om molngrenar i Adobe Commerce

I den här artikeln beskrivs hur du kan ordna om molngrenar på Adobe Commerce, om de inte är ordnade enligt rätt hierarki. Om du inte har grenarna ordnade i rätt hierarki kommer du inte att kunna sammanfoga till rätt överordnad gren - den kommer att gå till den befintliga överordnade grenen.

## Berörda produkter och versioner:

* Adobe Commerce om molninfrastruktur, 2.3.0-2.3.7-p2, 2.4.0-2.4.3-p1

## Organisationer av molntjänster

Rätt hierarkiorganisation för dina grenar är:

* [!DNL Master [main] > Production > Staging > Integration]
* [!DNL Master [main] > Production > Staging > Integration2]

## Lösning för felaktig organisation av molngrenar

Så här ordnar du om molngrenar:

1. Du måste ha [[!DNL Super User]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) roll.
1. Installera magento-cloud [!DNL CLI] (om du inte har gjort det).
1. Kör följande kommando för grenarna som behöver flyttas:
   `magento-cloud environment:info -e <branch to move> parent <target parent>`

Obs! Du kan ange den överordnade grenen när du skapar en ny gren. Om du vill se steg går du till [Komma igång med att skapa grenar](https://devdocs.magento.com/cloud/env/environments-start.html#getstarted) i vår dokumentation för utvecklare.

Du kan skapa en ny miljögren med `branch <environment-name> <parent-environment-ID>` magento-cloud environment command.

Det kan ta ytterligare tid att skapa och aktivera en ny miljögren.

## Relaterad läsning

[Hantera grenar med [!DNL CLI]](https://devdocs.magento.com/cloud/env/environments-start.html) i vår dokumentation för utvecklare.
