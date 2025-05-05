---
title: Indexen har gjorts ogiltiga och "indexer_reindex_all_invalid" körs hela tiden
description: Indexen har gjorts ogiltiga och "indexer_reindex_all_invalid" körs hela tiden
labels: troubleshooting,error,indexing,crons,site performance,adobe commerce,magento,cron,indexer_reindex_all_invalid,SQL,MySQL,reindex
exl-id: c7148ef4-2155-4d4c-869b-1d08de4af598
feature: B2B, Catalog Management, Categories, Observability, Price Indexer
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# Indexen har gjorts ogiltiga och `indexer_reindex_all_invalid` körs hela tiden

Den här artikeln innehåller en möjlig lösning på problemet när webbplatsen har prestandaproblem som orsakas av konstant omindexering. Detta orsakas av att [!DNL cron]-jobbet `indexer_reindex_all_invalid` körs kontinuerligt och cacheminnen rensas på [!DNL reindex].

## Berörda produkter och versioner

* Adobe Commerce (moln och lokalt) 2.4.0+ (Eftersom **[!UICONTROL Category Permissions]** endast är en funktion för Adobe-Commerce kommer den inte att påverka Magento Open Source.)

## Problem

I [!DNL New Relic One]-felloggarna ska visa `indexer_update_all_views` som körs många gånger med en tid på > 1 sekund (d.v.s. bearbetar något).

## Orsak

När Adobe Commerce-huvudimportprogrammet körs (manuellt eller av [!DNL cron]) utförs en uppsättning plugin-program för flera kärnmoduler för att avgöra vilka index som ska ogiltigförklaras.

Problemet inträffar när modulen **[!UICONTROL Category Permissions]** är aktiverad i [!DNL Commerce Admin]. Om detta är sant, ogiltigförklaras alltid indexen för produkt och kategori (och länkade index) i modulen när en import utförs. Om standardimporttyperna undersöks kommer alla att påverka **[!UICONTROL Category Permissions]**. Invalidering förväntas.

När en plats har B2B-moduler aktiverade aktiveras den dessutom om **[!UICONTROL Shared Catalog]** aktiveras och **[!UICONTROL Category Permissions]** låses. Om du stänger av **[!UICONTROL Shared Catalog]** låses **[!UICONTROL Category Permissions]** upp, men det stängs inte av.

<u>Kontrollerar [!DNL cron] loggar i din [!DNL MySQL]-databas</u>:

Om du loggar in i din [!DNL MySQL]-databas kan de söka efter **[!DNL reindex all indexes]**-processen i din `cron`-logg.
**ska** visas flera gånger, men den viktiga faktorn är att processen gör en av två möjliga saker.

Processen kan bara göra något av följande:

1. Ingenting: Det tar 0 till 1 sekund (en sekund eller mindre). Processen kontrollerar om den behöver göra något och stoppar sedan om den inte behöver göra något.
1. [!DNL Reindex] allt: Det tar alltid tid - vanligtvis minuter.

Vanligtvis vill du se många förekomster av processen, men med en körningstid på mindre än 1 sekund.
En handlare kan därför använda den här [!DNL MySQL]-frågan för att hitta transaktioner som tar **mer än 1 sekund** att köra:

```sql
SELECT TIMESTAMPDIFF(SECOND, executed_at, finished_at) AS period FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' HAVING period > 1
```

Du kan se hur lång tid en period spelas in genom att köra:

```sql
SELECT executed_at FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' AND executed_at IS NOT NULL ORDER BY executed_at ASC LIMIT 1;
```

Om detta inte ger dig tillräckligt lång tid för att göra en korrekt bedömning kan du öka tiden som en lyckad `cron`-process sparas i loggen efter den här [[!DNL Cron] (schemalagda aktiviteter)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html?lang=sv-SE)-guiden och öka **[!DNL Success History Lifetime]**-värdet (standardvärdet är bara 60 minuter).


## Lösning

Utöka `Magento\CatalogPermissions\Model\Indexer\Plugin\Import` så att metoden `afterImportSource` exkluderar den anpassade importeraren.

```
    public function afterImportSource(\Magento\ImportExport\Model\Import $subject, $import)
    {
        if ($this->config->isEnabled() && $subject->getEntity() !== 'ENTITY_CODE') {
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Category::INDEXER_ID)->invalidate();
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Product::INDEXER_ID)->invalidate();
        }
        return $import;
    }
```

Där `ENTITY_CODE` är det värde som används för entitetsnamnparametern i filen `import.xml` för den anpassade importören.

## Relaterad läsning

[Konfigurera [!DNL cron] jobb](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html?lang=sv-SE) i konfigurationsguiden för Adobe Commerce-åtgärder.
