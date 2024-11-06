---
title: Ordna om molngrenar i Adobe Commerce
description: I den här artikeln beskrivs hur du kan ordna om molngrenar på Adobe Commerce, om de inte är ordnade enligt rätt hierarki. Om du inte har grenarna ordnade i rätt hierarki kommer du inte att kunna sammanfoga till rätt överordnad gren - den kommer att gå till den befintliga överordnade grenen.
exl-id: 4fc0de96-da66-4634-a38a-6a1536855f8f
feature: Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

1. Du måste ha rollen [[!DNL Super User]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).
1. Installera magento-cloud [!DNL CLI] (om du inte har gjort det).
1. Kör följande kommando för grenarna som behöver flyttas:
   `magento-cloud environment:info -e <branch to move> parent <target parent>`

Obs! Du kan ange den överordnade grenen när du skapar en ny gren. Anvisningar finns i [Komma igång med att skapa grenar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) i utvecklardokumentationen.

Du kan skapa en ny miljögren med miljökommandot `branch <environment-name> <parent-environment-ID>` magento-cloud.

Det kan ta ytterligare tid att skapa och aktivera en ny miljögren.

## Relaterad läsning

[Hantera grenar med  [!DNL CLI]](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) i utvecklardokumentationen.
