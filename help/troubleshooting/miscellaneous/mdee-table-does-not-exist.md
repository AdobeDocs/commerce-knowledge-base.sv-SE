---
title: Åtgärda data som inte har uppdaterats i  [!DNL Commerce Data Exporter] feeds och [!DNL cron] loggar fel med ändringsloggtabellen finns inte
description: Den här artikeln innehåller en lösning för att åtgärda datasynkroniseringsproblem som orsakas av användning av fel vy-ID i  [!DNL Commerce Data Exporter mview] prenumerationen.
feature: Data Import/Export, Saas, Logs
role: Developer
exl-id: 50f2223b-bfcf-4c3c-b0f1-dbcc4365edc2
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Det finns inga korrigeringsdata som har uppdaterats i [!DNL Commerce Data Exporter]-feeds och [!DNL cron] loggar fel med ändringsloggtabellen

Den här artikeln innehåller en lösning för att åtgärda datasynkroniseringsproblem som orsakas av att fel vy-ID används i prenumerationen [!DNL Data Exporter] [[!DNL Mview]](https://developer.adobe.com/commerce/php/development/components/indexing/#mview). Prenumerationen [!DNL Mview] används för att spåra ändringar i databastabeller.

## Berörda produkter och versioner

Adobe Commerce-instanser där anpassad kod har tillämpats på dataexportfunktionen (`commerce-data-exporter` eller `saas-exporter`). Felet uppstår om den installerade [[!DNL SaaS] dataexportversionen är 103.3.0](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes#release-6) eller senare och koden refererar direkt till `catalog_data_exporter_products`-indexet.

## Problem

Handlare kan upptäcka att datauppdateringar saknas i matningstabellerna för katalogen [!DNL Data Exporter] och se följande fel i [!DNL cron]-jobbloggarna:

```
[2024-05-27T19:00:04.627604+00:00] report.ERROR: Cron Job indexer_clean_all_changelogs has an error: Table catalog_data_exporter_products_cl does not exist. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":305135616,"emalloc_start":283210384} [] [] 
```

## Orsak

På grund av namnändringar i flödestabeller, index och ändringsloggtabeller i [!DNL Commerce Data Export] [version 103.3.0](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes#release-9) kanske [!DNL Mview]-prenumerationerna i anpassade tillägg som använder [!DNL Commerce Data Export] inte fungerar som de ska.

I det här fallet finns inte felet *table* eftersom tabellnamnet `catalog_data_exporter` ändrades till `cde_products_feed` och du har en egen kod som refererar till det gamla namnet i prenumerationen [!DNL Data Exporter Mview].

## Lösning

I det anpassade tillägget redigerar du konfigurationsfilen [!DNL Mview] (```./etc/mview.xml```) för att ändra tabellnamnet `catalog_data_exporter_products` till *`cde_products_feed`*.

I följande exempel visas koden som anger tabellerna som spåras av prenumerationen [!DNL Mview]:

```
<view id="cde_products_feed" class="Magento\CatalogDataExporter\Model\Indexer\ProductFeedIndexer" group="indexer">
     <subscriptions>
         <table name="custom_table" entity_column="product_id" />
     </subscriptions>
</view>
```

## Relaterad läsning

* [[!DNL SaaS] Versionsinformation om dataexporttillägg](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes) i Adobe Commerce dataexportguide för [!DNL SaaS]-tjänster
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
