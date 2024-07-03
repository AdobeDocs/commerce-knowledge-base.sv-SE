---
title: Det går inte att ändra sökmotorn med Commerce Admin (sökmotormenyn är inte tillgänglig)
description: Den här artikeln innehåller en lösning för att ändra Adobe Commerce Search Engine med Commerce Admin om fältet Sökmotor inte visas eller kryssrutan Använd systemvärde är nedtonad och inte tillgänglig.
exl-id: 5b0f728c-6a8d-446d-9553-5abc3d01e516
feature: Admin Workspace, Search, Variables
role: Developer
source-git-commit: 0ea7bbef7fec556f9a90151be9cf1077f5cfac45
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 0%

---

# Det går inte att ändra sökmotorn med Commerce Admin (sökmotormenyn är inte tillgänglig)

>[!WARNING]
>
> [Sökmotorn för MySQL-kataloger kommer att tas bort i Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Du måste ha konfigurerat värddatorn Elasticsearch innan du kan installera version 2.4.0.
> 
> Se:
> [Installera och konfigurera Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch).
> [Installera och konfigurera OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/opensearch)
> [Installera och konfigurera Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install)

Den här artikeln innehåller en lösning för att ändra Adobe Commerce Search Engine med Commerce Admin om **Sökmotor** fältet visas inte eller **Använd systemvärde** kryssrutan är nedtonad och inte tillgänglig.

I den här artikeln:

* [Berörda versioner](#affected-versions)
* [Ändra sökmotor med hjälp av Commerce Admin (steg)](#change-search-engine-using-magento-admin-steps)
* [Problem med Adobe Commerce lokalt](#magento-commerce-on-premise)
* [Adobe Commerce i molninfrastruktur](#magento-commerce-cloud)

## Berörda versioner

* Lokal Adobe Commerce: 2.4.X
* Adobe Commerce om molninfrastruktur:
   * Version: 2.4.X
   * Arkitektur för Starter och Pro
* MySQL, Elasticsearch, Opensearch, Live Search: alla versioner som stöds

## Ändra sökmotor med hjälp av administratören (steg)

1. Logga in på **[!UICONTROL Admin]** som administratör.
1. Till vänster på **[!UICONTROL Admin]** sidlist, klicka på **[!UICONTROL Stores]**.
1. Under **[!UICONTROL Settings]**, välja **[!UICONTROL Configuration]**.
1. Navigera till panelen till vänster under **[!UICONTROL Catalog],** och välja **[!UICONTROL Catalog]**.
1. Expandera **[!UICONTROL Catalog Search]** -avsnitt.    ![catalog_menu.png](assets/catalog_menu.png)
1. Gå till **[!UICONTROL Search Engine]** fält och ta bort markering från **[!UICONTROL Use system value]** kryssrutan.
1. Klicka på **[!UICONTROL Search Engine]** och välj ett av de tillgängliga alternativen som visas nedan.    ![search_engine_menu.png](assets/search_engine_menu.png)
1. Klicka på **[!UICONTROL Save Config]** i det övre högra hörnet på sidan.

## Problem med Adobe Commerce lokalt

### Problem 1: Fältet Sökmotor visas inte

När du öppnar **Katalogsökning** -avsnittet, **Sökmotor** -menyn visas inte alls.

![search_engine_not_displayed.png](assets/search_engine_not_displayed.png)

### Orsak: Butiksvyn är inte en standardkonfiguration

Butiksvyn för administratören har angetts till ett annat värde än *Standardkonfiguration*.

Sökmotorn är en global konfigurationsuppsättning på programnivå, inte på Store-scopet. Lager i ett Adobe Commerce-program kan inte använda olika sökmotorer.

### Lösning: Ange standardkonfiguration för butiksvyn

1. Logga in på **[!UICONTROL Admin]** som administratör.
1. Till vänster på **[!UICONTROL Admin]** sidlist, klicka på **[!UICONTROL Stores]**.
1. Navigera till **[!UICONTROL Settings]** och välja **[!UICONTROL Configuration]**.
1. Klicka på i det övre vänstra hörnet **[!UICONTROL Store View]** väljare och välj **[!UICONTROL *Standardkonfiguration *]**.
1. Klicka på **[!UICONTROL OK]** i bekräftelsedialogrutan för att godkänna ändringar i butiksvyn.

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

Om du byter till Elasticsearch 7 blir SEARCH\_CONFIGURATION-variabeln i resultatet `.magento.env.yaml` filen kan se ut så här:

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     elasticsearch_server_hostname: hostname
     elasticsearch_server_port: '12345'
     elasticsearch_index_prefix: magento
     elasticsearch_server_timeout: '15'
```

Om du byter till [OpenSearch (i 2.4.6 och senare)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/search-engine-shown-elasticsearch-despite-open-search) variabeln SEARCH\_CONFIGURATION i resultatet `.magento.env.yaml` filen kan se ut så här:

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: opensearch
     elasticsearch_server_hostname: hostname
     elasticsearch_server_port: '12345'
     elasticsearch_index_prefix: magento
     elasticsearch_server_timeout: '15'
```

Om du [växla till Live Search](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/error-opensearch-search-engine-doesnt-exist-falling-back-to-livesearch), variabeln SEARCH\_CONFIGURATION i resultatet `.magento.env.yaml` filen kan se ut så här:

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: livesearch
```

### Relaterad dokumentation

#### Support Knowledge Base

* [Aktivera Elasticsearch i molnet](/help/how-to/general/enable-elasticsearch-on-cloud.md)

#### Dokumentation för utvecklare

* [Konfigurera tjänsten Elasticsearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch.html)
* [Bygg och driftsätt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) (dokumentation om `.magento.env.yaml` konfigurationsfil)
* [Distribuera variabler](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) ([SEARCH\_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#search_configuration))
* [Tjänster](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) (dokumentation om `.magento/services.yaml` konfigurationsfil)
* [Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview)
