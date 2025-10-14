---
title: Index är låst av en annan process
description: Den här artikeln handlar om ett vanligt indexeringsproblem i Adobe Commerce där indexet är låst av en annan process och hoppas över.
exl-id: 542c714c-fad5-4f0e-9757-d90044c36bfc
feature: Catalog Management, Categories
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Index är låst av en annan process

Den här artikeln handlar om ett vanligt indexeringsproblem i Adobe Commerce där indexet är låst av en annan process och hoppas över.

## Berörda produkter och versioner

* Adobe Commerce 2.X

## Problem

Under en fullständig omindexering i CLI får du felmeddelandet: *&#39;Index är låst av en annan omindexeringsprocess. Hoppar över.&#39;* Med andra ord, när processen eller indextypen är låst, kan du inte indexera om just den låsta indextypen. Indexeringen hoppar alltid över den indextypen.

## Orsak

Det här felet kan inträffa om det tidigare indexet inte slutfördes korrekt. Några möjliga orsaker är:

* Processen avbröts av en annan process eller användare.
* Minnesgräns.
* MySQL-fel, som en timeout.
* Allvarligt PHP-fel under omindexeringen.

## Steg som ska återskapas

1. Säg till exempel att    ```bash    cataloginventory_stock ```    indextypen är låst.
1. När du försöker indexera om alla data genom att köra CLI-kommandot    ```bash    php bin/magento indexer:reindex    ``` får du följande utdataresultat:    ```bash    customer_grid index has been rebuilt successfully in 00:00:09    catalog_category_product index has been rebuilt successfully in 00:00:07    catalog_product_category index has been rebuilt successfully in 00:00:00    catalogrule_rule index has been rebuilt successfully in 00:00:05    catalog_product_attribute index has been rebuilt successfully in 00:00:04    cataloginventory_stock index is locked by another reindex process. Skipping.    catalog_product_price index has been rebuilt successfully in 00:00:01    catalogrule_product has been rebuilt successfully in 00:00:00    catalogsearch_fulltext index has been rebuilt successfully in 00:00:01    ```
1. Som du ser ovan finns    ```bash    cataloginventory_stock```    indexprocessen har hoppats över.


## Lösning

Du måste återställa indexstatusen och sedan försöka köra den nya indexeringsprocessen. Du måste köra kommandot för att återställa indexstatus:

```bash
bin/magento indexer:reset <index identifier>
```

Om du är osäker på vad indexidentifierarna (koden) är kan du visa dem med kommandot:

```bash
bin/magento indexer:info
```

För fullständighetens skull finns det alla möjliga kombinationer för systemspecifika index:

```bash
bin/magento indexer:reset design_config_grid;
bin/magento indexer:reset customer_grid;
bin/magento indexer:reset catalog_category_product;
bin/magento indexer:reset catalog_product_category;
bin/magento indexer:reset catalogrule_rule;
bin/magento indexer:reset catalog_product_attribute;
bin/magento indexer:reset cataloginventory_stock;
bin/magento indexer:reset catalog_product_price;
bin/magento indexer:reset catalogrule_product;
bin/magento indexer:reset catalogsearch_fulltext;
```


## Relaterad läsning

I vår kunskapsbas:

* [Kronuppgifter låser uppgifter från andra grupper (Adobe Commerce i molninfrastruktur)](/help/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.md)

I vår användarhandbok:

* [Indexhantering](https://experienceleague.adobe.com/sv/docs/commerce-admin/systems/tools/index-management?itm_source=merchdocs&itm_medium=search_page&itm_campaign=federated_search&itm_term=reindexing)

I vår utvecklardokumentation:

* [Indexeringsöversikt](https://developer.adobe.com/commerce/php/development/components/indexing/)
* [Bästa praxis för indexerare](https://experienceleague.adobe.com/sv/docs/commerce-operations/performance-best-practices/configuration)
* [Konfigurera och kör Cron](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs)
* [Hantera indexerare](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/cli/manage-indexers)
* [Indexeroptimering](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/)
