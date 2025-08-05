---
title: Dåliga prestanda i integreringsmiljöer
description: Den här artikeln innehåller en lösning på problemet med att Pro-integreringsmiljöerna och Starter-testmiljöer fungerar dåligt.
feature: Integration, Staging
role: Developer
exl-id: 46110dbc-2f54-4654-95e2-39e8ae1e6979
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Dåliga prestanda i integreringsmiljöer

Den här artikeln innehåller en lösning på problemet med att Pro-integreringsmiljöerna och Starter-testmiljöer fungerar dåligt.

## Berörda produkter och versioner:

* Adobe Commerce om molninfrastruktur (alla versioner)

## Problem

Din Pro-integreringsmiljö eller Starter-staging fungerar dåligt.

## Orsak

Beroende på storleken på katalogen/data eller kraven för integreringar/anpassningar från tredje part kan de tillgängliga resurserna i integreringsmiljöerna ha överskridits.

## Lösning

För att åtgärda prestandaproblem måste du se till att du följer de bästa metoderna för bästa prestanda i integreringsmiljön. Du kan också behöva begära en uppgradering av miljöerna för att förbättra integreringen.

Kontrollera först om miljön finns på [konfigurationen för förbättrad integrering](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242).

* [Pro Architecture](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Startarkitektur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

Kontrollera distributionsloggen på något av följande sätt.

### Metod 1:

Kör följande kommando med CLI i molnet:

`magento-cloud activity:log -e <branch name>`

### Metod 2:

Kontrollera den senaste distributionsloggen för den miljön i [molnkonsolen](https://console.adobecommerce.com).

Om du ser något liknande i slutet av distributionsloggen, den första raden som visar storleken=XL, och de återstående raderna visar storleken=L, innebär det att du använder konfigurationen Förbättrad integrering.

```
Environment configuration
mymagento (type: php:8.2, size: XL, disk: 5120)
mysql (type: mysql:10.6, size: L, disk: 5120)
redis (type: redis:7.2, size: L)
opensearch (type: opensearch:2, size: L, disk: 1024)
rabbitmq (type: rabbitmq:3.12, size: L, disk: 1024)
```

Om du inte har den förbättrade integreringskonfigurationen kan du [begära en förbättring/uppgradering](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242).
Om du redan använder konfigurationen Förbättrad integrering eller fortfarande stöter på prestandaproblem efter uppgraderingen bör du följa de bästa metoderna för optimala prestanda i integreringsmiljön:

* [Pro Architecture](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Startarkitektur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

Om du har uppfyllt ovanstående rekommendationer [skickar du en supportförfrågan](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) för ytterligare hjälp.
