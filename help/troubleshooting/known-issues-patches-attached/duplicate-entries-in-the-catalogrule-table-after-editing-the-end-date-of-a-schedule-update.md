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

I den här artikeln finns en patch för det kända Adobe Commerce 2.2.3-problemet där redigering av slutdatum eller sluttid för en uppdatering av en katalogprisregel resulterar i att dubblettposter läggs till i `catalogrule` tabellen och fel i `catalogrule_rule` (Katalogregelprodukt) indexeraren indexeras om.

## Problem

När du ändrar slutdatum eller sluttid för en befintlig uppdatering av katalogens prisregelschema skapas dubblettposter i `catalogrule` databastabell. Resultatet blev att `catalogrule_rule` reindex misslyckas med följande fel i undantagsloggen: *Det finns redan ett objekt med samma ID*.

<u>Steg som ska återskapas</u>:

Krav: `catalogrule_rule` indexeraren har värdet *[Uppdatera enligt schema](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html)* läge.

1. Skapa en ny katalogprisregel under Commerce Admin **Marknadsföring** > **Erbjudanden** > **Katalogprisregel**.
1. I **Katalogprisregel** stödraster, klicka **Redigera** och schemalägga en ny uppdatering och uppsättning **Status** till *Aktiv.*
1. Klicka **Visa/redigera** bredvid den nyligen skapade uppdateringen och ändra slutdatumet till en tidigare tidpunkt.
1. Spara uppdateringen.
1. Kör kommandot reindex för `catalogrule_rule` indexerare.

<u>Förväntat resultat</u>:

The `catalogrule_rule` indexeraren har indexerats om. Inga dubblettposter i `catalogrule` tabell.

<u>Faktiskt resultat</u>:

Indexeringen misslyckas med följande fel: *Det finns redan ett objekt med samma ID*, eftersom det finns dubblettposter i `catalogrule` tabell.

## Lösning

För att lösa problemet måste du tillämpa den bifogade korrigeringen och ta bort de befintliga dubblettposterna. Se [Ta bort dubblettposter](#remove) om du vill ha information om hur du kontrollerar om dubbletterna finns och tar bort dem.

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

Se [Använda en kompositkorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) för instruktioner i vår kunskapsbas för support.

## Ta bort dubblettposter {#remove}

>[!NOTE]
>
>Se till att du har en säkerhetskopia nyligen innan du ändrar något.

Så här letar du reda på de duplicerade posterna och tar bort dem:

1. Kör följande fråga för att kontrollera om de duplicerade posterna finns i databasen:

   ```SQL
   SELECT entity_id, "catalog_product_entity" AS entity_table FROM catalog_product_entity GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT entity_id, "catalog_product_entity" AS entity_table FROM catalog_product_entity group by entity_id, updated_in having count(*) > 1    UNION    SELECT rule_id as entity_id, "catalogrule" AS entity_table FROM catalogrule GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "catalogrule" AS entity_table FROM catalogrule GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "salesrule" AS entity_table FROM salesrule GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "salesrule" AS entity_table FROM salesrule GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT page_id as entity_id, "cms_page" AS entity_table FROM cms_page GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT page_id as entity_id, "cms_page" AS entity_table FROM cms_page GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT block_id as entity_id, "cms_block" AS entity_table FROM cms_block GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT block_id as entity_id, "cms_block" AS entity_table FROM cms_block GROUP BY entity_id, updated_in HAVING COUNT(*) > 1;
   ```

   Om det inte finns några dubblettposter kommer svaret att vara tomt och du behöver inte göra något annat. Om de duplicerade posterna finns får du tabellnamnet och `entity_id` av den duplicerade entiteten, som i följande exempel:

   ![table_results1.png](assets/table_results1.png)

   Tänk på att i vissa tabeller kommer namnet på fältet med enhets-ID att skilja sig från `entity_id`. I `cms_page` bord, det skulle vara `page_id` i stället för `entity_id`.

1. Därefter måste du titta närmare på dubbletterna och förstå vilka som ska tas bort. Använd en fråga som liknar följande för att se dubbletterna. Ersätt registernamnet, enhets-ID:t och värdet enligt resultaten från föregående steg.

   ```sql
   SELECT row_id, entity_id, created_in, updated_in FROM catalog_product_entity WHERE entity_id = 483 ORDER BY created_in;
   ```

   Du får en lista med poster med flera kolumner. Exempel:

   ![table_results2.png](assets/table_results2.png)

   The `created_in` och `updated_in` värdena ska följa detta mönster: `created_in` värdet för den aktuella raden är lika med `updated_in` värdet i föregående rad. Dessutom finns **första raden** ska innehålla created\_in = 1 och **sista raden** ska innehålla uppdaterad\_in = 2147483647. (Om det bara finns en rad måste du se created\_in=1 **och** uppdaterad\_in=2147483647). Raden/raderna som mönstret bryts för bör tas bort. I vårt exempel är det raden med `row_id` =2052 som den andra och den tredje raden har båda samma värde för created_in: 1540837826, vilket inte ska ske.

1. Ta bort dubbletten med en fråga som liknar den nedan. Ersätt registernamnet, enhets-ID:t och värdet enligt resultaten från föregående steg:

   ```sql
   DELETE FROM catalog_product_entity WHERE entity_id = 483 AND row_id = 2052;
   ```

1. Rensa cache genom att köra:

   ```bash
   bin/magento cache:clean
   ```

   eller i Commerce Admin under **System** > **verktyg** > **Cachehantering**.

## Användbara länkar i vår utvecklardokumentation

* [Använd anpassade korrigeringsfiler för Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)
* [Visa och hantera loggar för Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html))

## Bifogade filer
