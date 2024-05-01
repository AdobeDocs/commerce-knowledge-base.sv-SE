---
title: Det går inte att ändra sökmotorn med Commerce Admin (sökmotormenyn är inte tillgänglig)
description: Den här artikeln innehåller en lösning för att ändra Adobe Commerce Search Engine med Commerce Admin om fältet Sökmotor inte visas eller kryssrutan Använd systemvärde är nedtonad och inte tillgänglig.
exl-id: 5b0f728c-6a8d-446d-9553-5abc3d01e516
feature: Admin Workspace, Search, Variables
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# Det går inte att ändra sökmotorn med Commerce Admin (sökmotormenyn är inte tillgänglig)

>[!WARNING]
>
> [Sökmotorn för MySQL-kataloger kommer att tas bort i Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Du måste ha konfigurerat värddatorn Elasticsearch innan du kan installera version 2.4.0. Se [Installera och konfigurera Elasticsearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch.html).

Den här artikeln innehåller en lösning för att ändra Adobe Commerce Search Engine med Commerce Admin om **Sökmotor** fältet visas inte eller **Använd systemvärde** kryssrutan är nedtonad och inte tillgänglig.

I den här artikeln:

* [Berörda versioner](#affected-versions)
* [Ändra sökmotor med hjälp av Commerce Admin (steg)](#change-search-engine-using-magento-admin-steps)
* [Problem med Adobe Commerce lokalt)](#magento-commerce-on-premise)
* [Adobe Commerce i molninfrastruktur](#magento-commerce-cloud)

## Berörda versioner

* Lokal Adobe Commerce: 2.X.X
* Adobe Commerce om molninfrastruktur:
   * Version: 2.X.X
   * Arkitektur för Starter och Pro
* MySQL, Elasticsearch: alla versioner som stöds

## Ändra sökmotor med hjälp av administratören (steg)

1. Logga in på administratören som administratör.
1. På vänster sida i administratörssidlisten klickar du på **Lager**. Sedan, under **Inställningar**, välja **Konfiguration**.
1. På panelen till vänster under **Katalog,** välj **Katalog**.
1. Expandera **Katalogsökning** -avsnitt.    ![catalog_menu.png](assets/catalog_menu.png)
1. Gå till **Sökmotor** fält och ta bort markering från **Använd systemvärde** kryssrutan.
1. Klicka på **Sökmotor** och välj ett av de tillgängliga alternativen.    ![search_engine_menu.png](assets/search_engine_menu.png)
1. Klicka **Spara konfiguration** i sidans övre högra hörn.

## Problem med Adobe Commerce lokalt

### Problem 1: Fältet Sökmotor visas inte

När du öppnar **Katalogsökning** -avsnittet, **Sökmotor** -menyn visas inte alls.

![search_engine_not_displayed.png](assets/search_engine_not_displayed.png)

### Orsak: Butiksvyn är inte en standardkonfiguration

Butiksvyn för administratören har angetts till ett annat värde än *Standardkonfiguration*.

Sökmotorn är en global konfigurationsuppsättning på programnivå, inte på Store-scopet. Lager i ett Adobe Commerce-program kan inte använda olika sökmotorer.

### Lösning: Ange standardkonfiguration för butiksvyn

1. Logga in på administratören som administratör.
1. På vänster sida i administratörssidlisten klickar du på **Lager**. Sedan, under **Inställningar**, välja **Konfiguration**.
1. Klicka i det övre vänstra hörnet på **Butiksvy** väljare och välj *Standardkonfiguration*.
1. Klicka **OK** i bekräftelsedialogrutan för att godkänna ändringen av butiksvyn.

![change_store_view.png](assets/change_store_view.png)

**Relaterad dokumentation:** [Ändra omfång](https://experienceleague.adobe.com/docs/commerce-admin/config/scope-change.html#set-the-scope) i vår användarhandbok.

### Problem 2: Det går inte att avmarkera Använd systemvärde

När du öppnar **Katalogsökning** -avsnittet i Admin, **Använd systemvärde** kryssrutan är nedtonad så att du inte kan ta bort markeringen från kryssrutan för att senare ändra sökmotorn.

### Orsak

Standardsökmotorn har konfigurerats på programkonfigurationsnivån i `app/etc/env.php` eller `app/etc/config.php` och kan därför inte ändras med Admin.

Exempel på avsnittet med standardkonfiguration för sökmotor:

```php
'system'=>
array (
'default'=>
array (
'catalog'=>
array (
'search'=>
array (
'engine'=>'mysql',
),
),
),
),
```

### Lösning

Ta bort avsnittet med standardsökmotorkonfigurationen från `app/etc/env.php` eller `app/etc/config.php` konfigurationsfiler.

### Relaterade artiklar i vår utvecklardokumentation

[Adobe Commerce konfigurationsfiler](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/files/deployment-files.html) i Adobe Commerce Configuration Guide

## Adobe Commerce i molninfrastruktur

Det går inte att växla sökmotorer med Admin i Adobe Commerce i molninfrastruktur på grund av hur molninfrastrukturen har organiserats.

Under distributionsprocessen kontrollerar Adobe Commerce-skript för molninfrastruktur om Elasticsearch har deklarerats i `MAGENTO_CLOUD_RELATIONSHIPS` variabel. Om den deklareras väljs Elasticsearch som aktiv sökmotor och konfigureras automatiskt. [MySQL-sökmotor](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md) blir oåtkomligt i Admin. Om relationen Elasticsearch inte har deklarerats anges MySQL till active och Elasticsearch blir otillgänglig.

Du bör inte redigera `app/etc/env.php` eller `app/etc/config.php` konfigurationsfiler direkt i molnmiljön. Det är därför som ändringar av dessa filer för att göra så att motorn Elasticsearch visas i Admin (den lösning vi rekommenderar i föregående avsnitt) inte gäller för ditt molnprojekt.

### Ändra sökmotor i miljöer för förproduktion och produktion

Innan du byter sökmotor från MySQL till Elasticsearch i dina miljö för förproduktion och produktion bör du kontrollera att du tidigare har [skickade en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) att aktivera Elasticsearch i miljön och biljetten har lösts.

Om du vill ändra sökmotorn som används i mellanlagrings- och produktionsmiljöer ändrar du `SEARCH_CONFIGURATION` systemvariabel i `.magento.env.yaml` i din lokala miljö och sedan överföra ändringarna till miljö för integrering och mellanlagring/produktion för att ändringarna ska börja gälla.

Om du byter från MySQL till Elasticsearch används variabeln SEARCH\_CONFIGURATION i resultatet `.magento.env.yaml` filen kan se ut så här:

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: elasticsearch
     elasticsearch_server_hostname: hostname
     elasticsearch_server_port: '123456'
     elasticsearch_index_prefix: magento
     elasticsearch_server_timeout: '15'
```

### Relaterad dokumentation

#### Support Knowledge Base

* [Aktivera Elasticsearch i molnet](/help/how-to/general/enable-elasticsearch-on-cloud.md)

#### Dokumentation för utvecklare

* [Konfigurera tjänsten Elasticsearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch.html)
* [Bygg och driftsätt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) (dokumentation om `.magento.env.yaml` konfigurationsfil)
* [Distribuera variabler](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) ([SEARCH\_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#search_configuration))
* [Tjänster](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) (dokumentation om `.magento/services.yaml` konfigurationsfil)
