---
title: Duplicera poster i katalogtabellen efter redigering av slutdatum för en schemauppdatering
description: Den här artikeln innehåller en patch för det kända Adobe Commerce 2.2.3-problemet där redigering av slutdatum eller sluttid för en uppdatering av en katalogprisregel resulterar i att dubblettposter läggs till i tabellen "catalogrle" och fel i indexeraren "catalogrle_rule" (produkt för katalogregel).
exl-id: e900b712-d0f5-4404-8441-64522035ce44
feature: Cache, Catalog Management, Marketing Tools
role: Developer
source-git-commit: 496151d1fe29a66d84349e4a96e7c5563a92c5c4
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# Duplicera poster i katalogtabellen efter redigering av slutdatum för en schemauppdatering

I den här artikeln finns en patch för det kända Adobe Commerce 2.2.3-problemet där redigering av slutdatum eller sluttid för en uppdatering av en katalogprisregel resulterar i att dubblettposter läggs till i tabellen `catalogrule` och fel i indexeraren för `catalogrule_rule` (katalogregelprodukten) läggs till.

## Problem

När du ändrar slutdatum eller sluttid för en befintlig uppdatering av katalogens prisregelschema skapas dubblettposter i databastabellen `catalogrule`. Därför misslyckas omindexeringen `catalogrule_rule` med följande fel i undantagsloggen: *Objektet med samma ID finns redan*.

<u>Steg som ska återskapas</u>:

Förutsättningar: Indexeraren `catalogrule_rule` är inställd på läget *[Uppdatera i schemat](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html)*.

1. I Commerce Admin skapar du en ny katalogprisregel under **Marknadsföring** > **Kampanjer** > **Katalogprisregel**.
1. Klicka på **Redigera** i rutnätet **Katalogprisregel** och schemalägg en ny uppdatering och ange **Status** till *Aktiv.*
1. Klicka på **Visa/redigera** bredvid den nyligen skapade uppdateringen och ändra slutdatumet till en tidigare tidpunkt.
1. Spara uppdateringen.
1. Kör indexeringskommandot för indexeraren `catalogrule_rule`.

<u>Förväntat resultat</u>:

Indexeraren `catalogrule_rule` har indexerats om. Inga dubblettposter i tabellen `catalogrule`.

<u>Faktiskt resultat</u>:

Indexeringen misslyckas med följande fel: *Det finns redan ett objekt med samma ID* eftersom det finns dubblettposter i tabellen `catalogrule`.

## Lösning

För att lösa problemet måste du tillämpa den bifogade korrigeringen och ta bort de befintliga dubblettposterna. Mer information om hur du kontrollerar om dubbletter finns och tar bort dubbletter finns i avsnittet [Ta bort dubblettposter](#remove).

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[Hämta MDVA-10974\_EE\_2.2.3\_COMPOSER\_v2.patch](assets/MDVA-10974_EE_2.2.3_COMPOSER_v2.patch.zip)

### Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce 2.2.3

Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce om molninfrastruktur 2.2.1 - 2.2.5
* Adobe Commerce lokal 2.2.1 - 2.2.2 och 2.2.4 - 2.2.5

## Så här sätter du på plåstret

Mer information finns i [Använda en dispositionsruta från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.

## Ta bort dubblettposter {#remove}

>[!NOTE]
>
>Se till att du har en säkerhetskopia nyligen innan du ändrar något.

Så här letar du reda på de duplicerade posterna och tar bort dem:

1. Kör följande fråga för att kontrollera om de duplicerade posterna finns i databasen:

   ```SQL
   SELECT entity_id, "catalog_product_entity" AS entity_table FROM catalog_product_entity GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT entity_id, "catalog_product_entity" AS entity_table FROM catalog_product_entity group by entity_id, updated_in having count(*) > 1    UNION    SELECT rule_id as entity_id, "catalogrule" AS entity_table FROM catalogrule GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "catalogrule" AS entity_table FROM catalogrule GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "salesrule" AS entity_table FROM salesrule GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "salesrule" AS entity_table FROM salesrule GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT page_id as entity_id, "cms_page" AS entity_table FROM cms_page GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT page_id as entity_id, "cms_page" AS entity_table FROM cms_page GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT block_id as entity_id, "cms_block" AS entity_table FROM cms_block GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT block_id as entity_id, "cms_block" AS entity_table FROM cms_block GROUP BY entity_id, updated_in HAVING COUNT(*) > 1;
   ```

   Om det inte finns några dubblettposter kommer svaret att vara tomt och du behöver inte göra något annat. Om det finns dubblerade poster får du tabellnamnet och `entity_id` för den duplicerade entiteten, som i följande exempel:

   ![table_results1.png](assets/table_results1.png)

   Tänk på att i vissa tabeller kommer namnet på fältet med enhets-ID att skilja sig från `entity_id`. I tabellen `cms_page` skulle det till exempel vara `page_id` i stället för `entity_id`.

1. Därefter måste du titta närmare på dubbletterna och förstå vilka som ska tas bort. Använd en fråga som liknar följande för att se dubbletterna. Ersätt registernamnet, enhets-ID:t och värdet enligt resultaten från föregående steg.

   ```sql
   SELECT row_id, entity_id, created_in, updated_in FROM catalog_product_entity WHERE entity_id = 483 ORDER BY created_in;
   ```

   Du får en lista med poster med flera kolumner. Exempel:

   ![table_results2.png](assets/table_results2.png)

   Värdena `created_in` och `updated_in` ska följa det här mönstret: värdet `created_in` för den aktuella raden är lika med värdet `updated_in` i föregående rad. Dessutom ska den **första raden** innehålla created\_in = 1 och den **sista raden** innehålla updated\_in = 2147483647. (Om det bara finns en rad måste du se created\_in=1 **och** updated\_in=2147483647). Raden/raderna som mönstret bryts för bör tas bort. I det här exemplet är det raden med `row_id` =2052 eftersom den andra och den tredje raden båda har samma värde för created_in: 1540837826, vilket inte ska ske.

1. Ta bort dubbletten med en fråga som liknar den nedan. Ersätt registernamnet, enhets-ID:t och värdet enligt resultaten från föregående steg:

   ```sql
   DELETE FROM catalog_product_entity WHERE entity_id = 483 AND row_id = 2052;
   ```

1. Rensa cache genom att köra:

   ```bash
   bin/magento cache:clean
   ```

   eller i Commerce Admin under **System** > **Verktyg** > **Cachehantering**.

## Användbara länkar i vår utvecklardokumentation

* [Använd anpassade korrigeringsfiler för Adobe Commerce i molninfrastrukturen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)
* [Visa och hantera loggar för Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html))

## Bifogade filer
