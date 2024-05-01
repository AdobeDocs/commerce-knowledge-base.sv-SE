---
title: Felsöka produktmodulen Recommendations i Adobe Commerce
description: Den här artikeln handlar om felsökningsförslag för
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: b20ad74194bacb09116131f4a8da1006da75738a
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Felsöka produktmodulen Recommendations i Adobe Commerce

Den här artikeln handlar om felsökningsförslag för

```php
magento/product-recommendations
```

och dess beroende

```php
saas-export
```

eftersom du behöver båda modulerna för att kunna använda verktyget Recommendations i Adobe Commerce.

## Berörda produkter och versioner

* Adobe Commerce 2.4.4 - 2.4.7

## Felsöka modulen för produktrekommendationer

Om du har konfigurerat

```php
magento/product-recommendations
```

modulen korrekt (kontrollera [Recommendations - installera och konfigurera Recommendations](https://devdocs.magento.com/recommendations/install-configure.html) i vår utvecklardokumentation.), men du kan inte se några rekommendationer, prova följande:

* Det är möjligt att modulen inte har haft tillräckligt med tid för att samla in beteendedata. Låt systemet köras i 24 timmar så att det kan börja samla in data. Överväg att distribuera en rekommendationstyp som inte kräver beteendedata, till exempel&quot;Mer sådant&quot;.

* Om du inte ser de rekommendationer som du har konfigurerat kan det finnas otillräckligt med data för att skapa rekommendationer för användaren.

* Kontrollera att SaaS-datamängden eller API-nyckeln är giltiga. Om du får ett felmeddelande när du har angett ditt SaaS-datautrymme eller din API-nyckel när produktrekommendationerna initieras kontrollerar du att du har angett [SaaS Data Space och API-nyckel](https://docs.magento.com/user-guide/configuration/services/saas.html) (i vår användarhandbok) korrekt. För att säkerställa att nyckeln för MageID och API är länkad måste den användare som äger MageID, vanligtvis den användare som äger Adobe Commerce-licensen, vara samma användare som genererar API-nyckeln. Om du måste ändra det MageID som användes [skicka ett supportärende](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

>[!NOTE]
>
>If [Begränsningsläge för cookie](https://docs.magento.com/m2/ce/user_guide/stores/compliance-cookie-restriction-mode.html) (i vår användarhandbok) är aktiverat samlar Adobe Commerce inte in beteendedata förrän kunden godkänner det. Om läget för cookie-begränsning är inaktiverat samlar Adobe Commerce in beteendedata som standard.

## Exporteringsmodulen för katalog-SaaS

För problem med katalogexport (

```php
saas-export
```

):

1. Bekräfta [cron](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cron.html) (i vår utvecklardokumentation) körs jobb.
1. Bekräfta [indexerare](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html) (i vår utvecklardokumentation) körs och    ```php    Product Feed    ```    indexeraren har värdet    ```php    Update by Schedule    ```    .
1. Bekräfta att modulerna är aktiverade. The    ```php    saas-export    ```    metapackage installerar följande moduler, som alla måste aktiveras:    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. Kontrollera [loggar](https://devdocs.magento.com/guides/v2.3/config-guide/cli/logging.html) (i vår dokumentation för utvecklare). Kontrollera att inga fel är associerade med ovanstående moduler.
1. Uppdatera cacheminnet för konfiguration. Gå till **System** > **verktyg** > **Cachehantering** och rensa konfigurationscachen.
1. Bekräfta att det finns data i    ```php    catalog_data_exporter_products    ```    databastabell.

## Händelser

[Rekommendationshändelser](https://devdocs.magento.com/recommendations/verify.html)I vår utvecklardokumentation beskrivs de beteendehändelser som skickas till Adobe Commerce.

## Relaterad läsning

* [Product Recommendations - Översikt](https://devdocs.magento.com/recommendations/product-recs.html) i vår utvecklardokumentation
* [Recommendations - installera och konfigurera Recommendations](https://devdocs.magento.com/recommendations/install-configure.html) i vår utvecklardokumentation
* [Marknadsföring - Recommendations](https://docs.magento.com/m2/ee/user_guide/marketing/product-recommendations.html) i vår användarhandbok
* [Skapa Recommendations](https://docs.magento.com/m2/ee/user_guide/marketing/create-new-rec.html) i vår användarhandbok
