---
title: Felsöka modulen [!UICONTROL Product Recommendations] i Adobe Commerce
description: Den här artikeln handlar om felsökningsförslag för modulen [!UICONTROL Product Recommendations] i Adobe Commerce.
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# Felsöka modulen [!UICONTROL Product Recommendations] i Adobe Commerce

Den här artikeln handlar om felsökningsförslag för

```php
magento/product-recommendations
```

och dess beroende

```php
saas-export
```

eftersom du behöver båda modulerna för att kunna använda verktyget [!UICONTROL Product Recommendations] i Adobe Commerce.

## Berörda produkter och versioner

* Adobe Commerce 2.4.4 - 2.4.7

## Felsöka modulen för produktrekommendationer

Om du har konfigurerat

```php
magento/product-recommendations
```

modul korrekt (Kontrollera [[!UICONTROL Product Recommendations - Install and Configure]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure) i utvecklardokumentationen.) men du ser inga rekommendationer, prova följande:

* Det är möjligt att modulen inte har haft tillräckligt med tid för att samla in beteendedata. Låt systemet köras i 24 timmar så att det kan börja samla in data. Överväg att distribuera en rekommendationstyp som inte kräver några beteendedata, till exempel *Mer som denna*.

* Om du inte ser de rekommendationer som du har konfigurerat kan det finnas otillräckligt med data för att skapa rekommendationer för användaren.

* Kontrollera att [!DNL SaaS]-datamängden eller [!DNL API]-nyckeln är giltiga. Om du får ett fel när du har angett ditt [!DNL SaaS]-datautrymme eller din [!DNL API]-nyckel under initieringen av produktrekommendationer kontrollerar du att du har angett [[!DNL SaaS] datautrymmet och [!DNL API] nyckeln](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) (i användarhandboken) korrekt. För att nyckeln [!DNL MageID] och [!DNL API] ska kunna länkas måste användaren som äger [!DNL MageID], vanligtvis den användare som äger Adobe Commerce-licensen, vara samma användare som genererar nyckeln [!DNL API]. Om du måste ändra [!DNL MageID] som användes [skickar du en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

>[!NOTE]
>
>Om [**[!UICONTROL Cookie Restriction Mode]**](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law) (i vår användarhandbok) är *aktiverad* samlar Adobe Commerce inte in beteendedata förrän kunden godkänner det. Om **[!UICONTROL Cookie Restriction Mode]**är *inaktiverad* samlar Adobe Commerce in beteendedata som standard.

## Exporteringsmodul för katalog [!DNL SaaS]

För problem relaterade till katalogexporten [!DNL SaaS] (

```php
saas-export
```

):

1. Bekräfta att jobben [[!DNL cron]](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) (i utvecklardokumentationen) körs.
1. Bekräfta att [[!UICONTROL indexers]](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers) (i utvecklardokumentationen) körs och att    ```php    Product Feed    ```    [!UICONTROL indexer] är inställt på    ```php    Update by Schedule    ```    .
1. Bekräfta att modulerna är *aktiverade*. The    ```php    saas-export    ```    metapackage installerar följande moduler, som alla måste vara *aktiverade* :    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. Kontrollera [loggarna](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/enable-logging) (i utvecklardokumentationen). Kontrollera att inga fel är associerade med ovanstående moduler.
1. Uppdatera [!UICONTROL Configuration cache]. Gå till **System** > **Verktyg** > **Cachehantering** och rensa [!UICONTROL Configuration cache].
1. Bekräfta att det finns data i databastabellen `cde_products_products_feed`.

   >[!NOTE]
   >
   >Om du inte kan hitta tabellen kontrollerar du tabellen `catalog_data_exporter_products`. Tabellnamnet ändrades i version 103.3.0 av [!DNL Data Export].

## Händelser

[Verifiera händelsesamling](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/verify) i utvecklardokumentationen, som beskriver de beteendehändelser som skickas till Adobe Commerce.

## Relaterad läsning

* [Produkt-Recommendations Administrator Development](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/development-overview) i utvecklardokumentationen
* [Introduktion till Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview) i Recommendations-handboken för produkten
* [Skapa produkt-Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/admin/create) i Recommendations-handboken för produkten
* [Granska loggar och felsök](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging) i [!DNL SaaS]-guiden för dataexport
* [[!DNL SaaS] Versionsinformation om dataexporttillägg](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes) i Adobe Commerce dataexportguide för [!DNL SaaS]-tjänster
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook

