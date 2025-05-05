---
title: Tilldela mer utrymme för MySQL i Adobe Commerce i molnet
description: I den här artikeln finns anvisningar om hur du tilldelar mer utrymme till MySQL i Adobe Commerce i molninfrastrukturen.
exl-id: 98501aa0-5ec7-4ea1-8856-13d171ad0be9
feature: Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Tilldela mer utrymme för MySQL i Adobe Commerce i molnet


## Allokera utrymme på Starter-planen och Pro-plansintegrering

För alla startplansmiljöer och Pro-planens [integreringsmiljö](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) kan du tilldela mer utrymme för MySQL i filen `.magento/services.yaml` genom att öka parametern `mysql: disk:`. Exempel:

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

Se artikeln [Konfigurera MySQL-tjänsten](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/configure/service/mysql) för referens.

När du har ändrat filen `.magento/services.yaml` måste du implementera och överföra dina ändringar för att de ska tillämpas. Tryckningen kommer att utlösa distributionsprocessen.

>[!WARNING]
>
>En startplanspartition bör aldrig göras mindre (till exempel från 30 GB till 20 GB) eftersom detta troligen kommer att leda till katastrofala dataskador.

## Allokera utrymme på Pro-planmellanlagring eller -produktion

Om du vill göra de här ändringarna för mellanlagrings- eller produktionsmiljön för Pro-planen måste du skapa en [supportbiljett](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed). När en supportanmälan skickas för att öka lagringsutrymmet måste supporten veta hur mycket och vilken partition som lagringsutrymmet ska användas på (`/mysql` eller `/exports`). En begäran om lagringsökning kräver godkännande från ditt kontoteam på Adobe, som granskar din lagringsmängd (enligt beställningsformuläret) innan de godkänner det.

## Minska tilldelat utrymme är inte tillgängligt (Pro- och Starter-plan)

Adobe Commerce Support kan utöka en partition (`/mysql` eller `/exports`), men kan inte krympa en partition. Det finns risk för att data skadas om du gör det. Det är därför lagringsutrymme för en partition inte är tillgängligt.
Det gäller också för Starter-planen, där du kan öka det tilldelade utrymmet själv: du bör inte minska det, vilket kan leda till att data skadas på ett katastrofalt sätt.
