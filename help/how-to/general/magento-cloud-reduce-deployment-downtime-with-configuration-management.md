---
title: Minska driftstoppen på Adobe Commerce i molninfrastrukturen
description: För att dramatiskt minska driftstoppen för underhåll och tillhandahålla effektiv konfigurering av din butik i olika miljöer erbjuder Adobe Commerce i molninfrastrukturen funktionen **Configuration Management**. För implementeringar av Adobe Commerce i molninfrastruktur 2.2.x och senare stöder den här funktionen koncept och alternativ för driftsättning i pipeline med reducerade steg.
exl-id: fde3571c-d95c-4a9b-a024-3b29f9c491ab
feature: Build, Cloud, Configuration, Deploy
source-git-commit: 23d957ceac17f9989d14b215582304199d398545
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Minska driftstoppen på Adobe Commerce i molninfrastrukturen

För att avsevärt minska driftstoppen för underhåll och tillhandahålla effektiv konfiguration av din butik i olika miljöer erbjuder Adobe Commerce i molninfrastrukturen funktionen **Configuration Management**. För implementeringar av Adobe Commerce i molninfrastruktur 2.2.x och senare stöder den här funktionen koncept och alternativ för driftsättning i pipeline med reducerade steg.

## Ökning

De svåra och tidsödande problemen med att distribuera din webbutik är bland annat:

* **Använder samma konfiguration i alla miljöer.** Vanligtvis anger du konfigurationer manuellt eller via komplicerade databasuppdateringar. Med Configuration Management exporterar du konfigurationer från databasen till en enda fil för att senare överföra den med koden från den lokala utvecklingsmiljön till Integration, Staging och Production.

* **Driftavbrott för webbplatsen vid distribution av statiskt innehåll.** Vanligtvis distribueras statiskt innehåll under [distributionsfasen](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase). Detta kan ta upp till 30 minuter eller mer, vilket inte är acceptabelt för företag. Konfigurationshanteringen flyttar statisk innehållsdistribution till [byggfasen](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase), som inte kräver driftstopp.

## Teknikversioner

* Adobe Commerce i molninfrastrukturen **2.1.4** och senare för Configuration Management
* Adobe Commerce i molninfrastrukturen **2.2** och senare för Configuration Management/Pipeline-distribution

## Vad är konfigurationshantering?

För att göra en lång historia kort extraherar konfigurationsprocessen (även kallad Pipeline Deployment) alla konfigurationsinställningar från din Adobe Commerce för molninfrastruktur (databas) till en enda PHP-fil. Sedan lägger du till filen i Git-implementeringen och kör den i alla dina miljöer.

Detta ger följande fördelar:

* **Enhetliga inställningar i alla miljöer:** Alla inställningar som exporteras till konfigurationsfilen blir låsta (motsvarande fält i Commerce Admin blir skrivskyddade), vilket ger enhetliga konfigurationer när du skickar filen över alla miljöer.
* **Minskad drifttid:** Den statiska fildistributionen växlar från [distributionsfasen](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase) (som kräver att platsen är i underhållsläge) till [byggfasen](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase) (när platsen inte är i underhållsläge och inte kommer att stängas ned om fel eller problem uppstår).
* **Skyddade känsliga data:** med Adobe Commerce i molninfrastruktur 2.2 och senare exporterar processen även känsliga data (till exempel autentiseringsuppgifter för betalningsgateway) till filen `env.php`. Den här filen bör bara sparas i den miljö som den skapades i och inte skickas med Git-grenarna.

Vi rekommenderar starkt att du tillämpar Configuration Management-metoden i din distribution.

## Konfigurationshantering i utvecklardokumentationen

* [Konfigurationshantering för **2.1.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=sv-SE) och [example](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=sv-SE) i *Adobe Commerce on cloud infrastructure Guide*
* [Konfigurationshantering för **2.2.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=sv-SE) och [example](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=sv-SE) i *Adobe Commerce on cloud infrastructure Guide*
* [Uppgradera från 2.0.X eller 2.1.X](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html?lang=sv-SE#upgrade-from-older-versions) i avsnittet *Uppgradera Adobe Commerce för molninfrastruktur*
* [Driftsättning av pipeline](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/overview.html?lang=sv-SE) i *konfigurationsguiden för molninfrastruktur för Adobe Commerce* - För Adobe Commerce om molninfrastruktur behöver du inte följa instruktionerna i den här guiden. Innehållet är avsett som referens. Vi tillhandahåller redan byggservern, integreringsmiljöer och mycket mer med Adobe Commerce i molninfrastrukturen.
