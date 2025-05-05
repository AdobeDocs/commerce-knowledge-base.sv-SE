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
> [MySQL-katalogsökmotorn tas bort i Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Du måste ha konfigurerat värddatorn Elasticsearch innan du kan installera version 2.4.0.
> 
> Se:
> [Installera och konfigurera Elasticsearch](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch).
> [Installera och konfigurera OpenSearch](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/configure/service/opensearch)
> [Installera och konfigurera Live Search](https://experienceleague.adobe.com/sv/docs/commerce-merchant-services/live-search/install)

Den här artikeln innehåller en lösning för att ändra Adobe Commerce Search Engine med Commerce Admin om fältet **Sökmotor** inte visas eller om kryssrutan **Använd systemvärde** är nedtonad och inte tillgänglig.

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
1. Klicka på **[!UICONTROL Stores]** till vänster om sidofältet **[!UICONTROL Admin]**.
1. Välj **[!UICONTROL Configuration]** under **[!UICONTROL Settings]**.
1. Navigera till panelen till vänster under **[!UICONTROL Catalog],** och välj **[!UICONTROL Catalog]**.
1. Expandera avsnittet **[!UICONTROL Catalog Search]**.    ![catalog_menu.png](assets/catalog_menu.png)
1. Gå till fältet **[!UICONTROL Search Engine]** och ta bort markeringen från kryssrutan **[!UICONTROL Use system value]**.
1. Klicka på menyn **[!UICONTROL Search Engine]** och välj ett av de tillgängliga alternativen som visas nedan.    ![search_engine_menu.png](assets/search_engine_menu.png)
1. Klicka på **[!UICONTROL Save Config]** längst upp till höger på sidan.

## Problem med Adobe Commerce lokalt

### Problem 1: Fältet Sökmotor visas inte

När du öppnar avsnittet **Katalogsökning** visas inte menyn **Sökmotor** alls.

![search_engine_not_displayed.png](assets/search_engine_not_displayed.png)

### Orsak: Butiksvyn är inte en standardkonfiguration

Butiksvyn för administratören har angetts till ett annat värde än *Standardkonfiguration*.

Sökmotorn är en global konfigurationsuppsättning på programnivå, inte på Store-scopet. Lager i ett Adobe Commerce-program kan inte använda olika sökmotorer.

### Lösning: Ange standardkonfiguration för butiksvyn

1. Logga in på **[!UICONTROL Admin]** som administratör.
1. Klicka på **[!UICONTROL Stores]** till vänster om sidofältet **[!UICONTROL Admin]**.
1. Navigera till **[!UICONTROL Settings]** och välj **[!UICONTROL Configuration]**.
1. Klicka på väljaren **[!UICONTROL Store View]** i det övre vänstra hörnet och välj **[!UICONTROL *Standardkonfiguration *]**.
1. Klicka på **[!UICONTROL OK]** i bekräftelsedialogrutan för att godkänna ändringarna i butiksvyn.

![change_store_view.png](assets/change_store_view.png)

**Relaterad dokumentation:** [Ändra omfång](https://experienceleague.adobe.com/docs/commerce-admin/config/scope-change.html?lang=sv-SE#set-the-scope) i vår användarhandbok.

### Problem 2: Det går inte att avmarkera Använd systemvärde

När du öppnar avsnittet **Katalogsökning** i Admin är kryssrutan **Använd systemvärde** nedtonad så att du inte kan ta bort markeringen från kryssrutan för att senare ändra sökmotorn.

### Orsak

Standardsökmotorn har konfigurerats på programkonfigurationsnivån i filerna `app/etc/env.php` eller `app/etc/config.php` och kan därför inte ändras med Admin.

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

Ta bort avsnittet med standardsökmotorkonfigurationen från `app/etc/env.php`- eller `app/etc/config.php`-konfigurationsfilerna.

### Relaterade artiklar i vår utvecklardokumentation

[Adobe Commerce konfigurationsfiler](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/files/deployment-files.html?lang=sv-SE) i Adobe Commerce Configuration Guide

## Adobe Commerce i molninfrastruktur

Det går inte att växla sökmotorer med Admin i Adobe Commerce i molninfrastruktur på grund av hur molninfrastrukturen har organiserats.

Under distributionsprocessen kontrollerar Adobe Commerce-skript för molninfrastruktur om Elasticsearch har deklarerats i variabeln `MAGENTO_CLOUD_RELATIONSHIPS`. Om den deklareras väljs Elasticsearch som aktiv sökmotor och konfigureras automatiskt. [MySQL-sökmotorn](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md) blir inte tillgänglig i Admin. Om relationen Elasticsearch inte har deklarerats anges MySQL till active och Elasticsearch blir otillgänglig.

Du bör inte redigera `app/etc/env.php`- eller `app/etc/config.php`-konfigurationsfilerna direkt i din molnmiljö. Det är därför som ändringar av de här filerna så att Elasticsearch-motorn visas i Admin (den lösning vi rekommenderar i föregående avsnitt) inte gäller för ditt molnprojekt.

### Ändra sökmotor i miljöer för förproduktion och produktion

Innan du byter sökmotor från MySQL till Elasticsearch i dina miljö för förproduktion och produktion bör du kontrollera att du tidigare har [skickat in en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) med en begäran om att aktivera Elasticsearch i miljön och att biljetten har lösts.

Om du vill ändra sökmotorn som används i dina miljö för förproduktion och produktion ändrar du miljövariabeln `SEARCH_CONFIGURATION` i din `.magento.env.yaml`-fil på den lokala miljön och sedan ändrar du miljöerna för integrering och förproduktion/produktion så att ändringarna börjar gälla.

Om du byter till Elasticsearch 7 kan SEARCH\_CONFIGURATION-variabeln i den resulterande `.magento.env.yaml`-filen se ut så här:

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

Om du byter till [Opensearch (i 2.4.6 och senare)](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/search-engine-shown-elasticsearch-despite-open-search) kan SEARCH\_CONFIGURATION-variabeln i den resulterande `.magento.env.yaml`-filen se ut så här:

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

Om du [byter till Live Search](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/error-opensearch-search-engine-doesnt-exist-falling-back-to-livesearch) kan SEARCH\_CONFIGURATION-variabeln i den resulterande `.magento.env.yaml`-filen se ut så här:

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

* [Konfigurera tjänsten Elasticsearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch.html?lang=sv-SE)
* [Skapa och distribuera](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html?lang=sv-SE) (dokumentation om konfigurationsfilen `.magento.env.yaml`)
* [Distribuera variabler](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=sv-SE) ([SEARCH\_CONFIGURATION-avsnittet](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=sv-SE#search_configuration))
* [Tjänster](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html?lang=sv-SE) (dokumentation om konfigurationsfilen `.magento/services.yaml`)
* [Live Search](https://experienceleague.adobe.com/sv/docs/commerce-merchant-services/live-search/overview)
