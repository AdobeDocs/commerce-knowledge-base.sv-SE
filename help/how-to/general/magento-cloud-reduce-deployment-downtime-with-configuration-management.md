---
title: Minska driftstoppen på Adobe Commerce i molninfrastrukturen
description: För att dramatiskt minska driftstoppen för underhåll och tillhandahålla effektiv konfigurering av din butik i olika miljöer erbjuder Adobe Commerce i molninfrastrukturen funktionen **Configuration Management**. För implementeringar av Adobe Commerce i molninfrastruktur 2.2.x och senare stöder den här funktionen koncept och alternativ för driftsättning i pipeline med reducerade steg.
exl-id: fde3571c-d95c-4a9b-a024-3b29f9c491ab
feature: Build, Cloud, Configuration, Deploy
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Minska driftstoppen på Adobe Commerce i molninfrastrukturen

För att avsevärt minska driftstoppen för underhåll och tillhandahålla effektiv konfigurering av din butik i olika miljöer erbjuder Adobe Commerce i molninfrastrukturen **Konfigurationshantering** -funktion. För implementeringar av Adobe Commerce i molninfrastruktur 2.2.x och senare stöder den här funktionen koncept och alternativ för driftsättning i pipeline med reducerade steg.

## Ökning

De svåra och tidsödande problemen med att distribuera din webbutik är bland annat:

* **Använder samma konfiguration i alla miljöer.** Normalt anger du konfigurationer manuellt eller via komplicerade databasuppdateringar. Med Configuration Management exporterar du konfigurationer från databasen till en enda fil för att senare överföra den med koden från den lokala utvecklingsmiljön till Integration, Staging och Production.

* **Driftavbrott för webbplatsen vid distribution av statiskt innehåll.** Vanligtvis distribueras statiskt innehåll under [distributionsfas](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase). Detta kan ta upp till 30 minuter eller mer, vilket inte är acceptabelt för företag. Configuration Management flyttar statisk innehållsdistribution till [byggfas](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?#build-phase), vilket inte kräver driftstopp.

## Teknikversioner

* Adobe Commerce i molninfrastruktur **2.1.4** och senare för Configuration Management
* Adobe Commerce i molninfrastruktur **2.2** och senare för Configuration Management/Pipeline Deployment

## Vad är konfigurationshantering?

För att göra en lång historia kort extraherar konfigurationsprocessen (även kallad Pipeline Deployment) alla konfigurationsinställningar från din Adobe Commerce för molninfrastruktur (databas) till en enda PHP-fil. Sedan lägger du till filen i Git-implementeringen och kör den i alla dina miljöer.

Detta ger följande fördelar:

* **Enhetliga inställningar i alla miljöer:** alla inställningar som exporteras till konfigurationsfilen blir låsta (motsvarande fält i Commerce Admin blir skrivskyddade), vilket ger enhetliga konfigurationer när du flyttar filen över alla miljöer.
* **Minskade driftstopp:** den statiska fildistributionen ändras från [distributionsfas](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase) (som kräver att platsen är i underhållsläge) till [byggfas](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?#build-phase) (när platsen inte är i underhållsläge och inte kommer att stängas av om fel eller problem uppstår).
* **Skyddade känsliga data:** med Adobe Commerce i molninfrastruktur 2.2 och senare exporterar processen även känsliga data (till exempel autentiseringsuppgifter för betalningstjänst) till `env.php` -fil. Den här filen bör bara sparas i den miljö som den skapades i och inte skickas med Git-grenarna.

Vi rekommenderar starkt att du tillämpar Configuration Management-metoden i din distribution.

## Konfigurationshantering i utvecklardokumentationen

* [Konfigurationshantering för **2.1.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) och [exempel](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) i *Adobe Commerce i molninfrastrukturguide*
* [Konfigurationshantering för **2.2.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) och [exempel](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) i *Adobe Commerce i molninfrastrukturguide*
* [Uppgradera från 2.0.X eller 2.1.X](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html#upgrade-from-older-versions) i *Uppgradera Adobe Commerce i molninfrastruktur* ämne
* [Driftsättning av pipeline](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/overview.html) i *Konfigurationshandbok för molninfrastruktur* - För Adobe Commerce om molninfrastruktur behöver du inte följa instruktionerna i den här guiden. Innehållet är avsett som referens. Vi tillhandahåller redan byggservern, integreringsmiljöer och mycket mer med Adobe Commerce i molninfrastrukturen.
