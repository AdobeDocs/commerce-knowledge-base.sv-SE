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

# Invaliderade och `indexer_reindex_all_invalid` hela tiden

Den här artikeln innehåller en möjlig lösning på problemet när webbplatsen har prestandaproblem som orsakas av konstant omindexering. Detta orsakas av [!DNL cron] jobb `indexer_reindex_all_invalid` oavbruten körning och cacheminnen rengjorda [!DNL reindex].

## Berörda produkter och versioner

* Adobe Commerce (molnet &amp; lokalt) 2.4.0+ (som **[!UICONTROL Category Permissions]** är en funktion som bara fungerar i Adobe-Commerce, som inte påverkar Magento Open Source.)

## Problem

I [!DNL New Relic One] felloggar bör visa `indexer_update_all_views` som körs många gånger med en tid på > 1 sekund (d.v.s. bearbetar något).

## Orsak

När den huvudsakliga Adobe Commerce-importfunktionen körs (manuellt eller av [!DNL cron]) körs en uppsättning plugin-program för flera kärnmoduler för att avgöra vilka index som ska ogiltigförklaras.

Problemet inträffar när **[!UICONTROL Category Permissions]** modulen är aktiverad i [!DNL Commerce Admin]. Om detta är sant, ogiltigförklaras alltid indexen för produkt och kategori (och länkade index) i modulen när en import utförs. Om standardimporttyperna undersöks påverkas alla **[!UICONTROL Category Permissions]**. Invalidering förväntas.

När en plats har B2B-moduler aktiverade kan dessutom **[!UICONTROL Shared Catalog]** är aktiverad, den aktiveras och låses **[!UICONTROL Category Permissions]**. Stänger av **[!UICONTROL Shared Catalog]** kommer att låsa upp **[!UICONTROL Category Permissions]**, men stäng inte av den.

<u>Kontrollerar [!DNL cron] loggar in på [!DNL MySQL] databas</u>:

Om du loggar in på [!DNL MySQL] databas kan de kontrollera `cron` loggar för **[!DNL reindex all indexes]** -processen.
Detta **bör** många gånger, men den viktiga faktorn är att processen gör något av två möjliga saker.

Processen kan bara göra något av följande:

1. Ingenting: Det tar 0 till 1 sekund (en sekund eller mindre). Processen kontrollerar om den behöver göra något och stoppar sedan om den inte behöver göra något.
1. [!DNL Reindex] allt: Det tar alltid tid - vanligtvis minuter.

Vanligtvis vill du se många förekomster av processen, men med en körningstid på mindre än 1 sekund.
En handlare kan därför använda detta [!DNL MySQL] fråga för att hitta transaktioner som **mer än en sekund** att köra:

```sql
SELECT TIMESTAMPDIFF(SECOND, executed_at, finished_at) AS period FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' HAVING period > 1
```

Du kan se hur lång tid en period spelas in genom att köra:

```sql
SELECT executed_at FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' AND executed_at IS NOT NULL ORDER BY executed_at ASC LIMIT 1;
```

Om detta inte ger er tillräckligt lång tid för att göra en riktig bedömning kan ni öka tiden för ett framgångsrikt `cron` processen sparas i loggen efter detta [[!DNL Cron] (schemalagda aktiviteter)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) och öka **[!DNL Success History Lifetime]** (standardvärdet är bara 60 minuter).


## Lösning

Utöka `Magento\CatalogPermissions\Model\Indexer\Plugin\Import` så att `afterImportSource` -metoden exkluderar den anpassade importeraren.

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

Plats `ENTITY_CODE` är värdet som används för enhetsnamnparametern i `import.xml` fil för den anpassade importören.

## Relaterad läsning

[Konfigurera [!DNL cron] jobb](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) i Adobe Commerce Operations Configuration Guide.
