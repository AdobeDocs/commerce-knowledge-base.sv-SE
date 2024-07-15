---
title: Elasticsearch 5 är konfigurerat, men söksidan läses inte in med felmeddelandet "FieldData is disabled...".
description: 'I det här avsnittet beskrivs hur du åtgärdar problemet med Elasticsearch 5, där söksidan inte läses in och undantaget som liknar följande genereras:'
exl-id: f5fa8144-4e7c-45ce-89d0-a8367e91d6db
feature: Cache
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Elasticsearch 5 är konfigurerat, men söksidan läses inte in med felmeddelandet &quot;FieldData is disabled...&quot;.

I det här avsnittet beskrivs hur du åtgärdar problemet med Elasticsearch 5, där söksidan inte läses in och undantaget som liknar följande genereras:

```bash
{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}].
```

## Berörda versioner

* Adobe Commerce 2.2.x
* Elasticsearch v.5

>[!NOTE]
>
>Elasticsearch v.5 används inte i Adobe Commerce 2.3.x

## Problem

Förvillkor: Elasticsearch 5 är konfigurerat.

Vid sökbegäran genereras följande undantag i loggar:

```bash
{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}].
```

## Orsak

Som standard kan endast vissa typer av produktattribut användas i Navigering i lager. De är Ja/Nej, Listruta, MultiplerSelect och Price. Det är därför du inte kan ange ett attribut av någon annan typ i Commerce Admin som **Använd i lagernavigering** = *Filterable* eller **Använd i lagernavigering i sökresultat** = *Yes* . Men det finns en teknisk möjlighet att kringgå den här begränsningen genom att ändra värdena `is_filterable` och `is_filterable_in_search` i databasen direkt. Om detta inträffar och någon annan attributtyp, t.ex. Datum, Text o.s.v., är inställd att användas i Navigering i lager, genereras ett undantag i Elasticsearch 5.

Om du vill vara säker på att så är fallet måste du ta reda på om det finns andra attribut än listruta, MultiplerSelect och Price som är inställda att användas i Navigering i lager. Sök efter attributen genom att köra följande fråga:

```sql
SELECT ea.attribute_code, ea.frontend_input, cea.is_filterable, cea.is_filterable_in_search FROM eav_attribute AS ea
    -> INNER JOIN catalog_eav_attribute AS cea ON ea.attribute_id = cea.`attribute_id`
    -> WHERE (is_filterable = 1 OR is_filterable_in_search = 1) AND frontend_input NOT IN ('boolean', 'multiselect', 'select', 'price');
```

Resultatet innehåller en lista med attribut som används för Navigering i lager, vars typ inte tillåter detta. Åtgärda problemet genom att utföra de steg som beskrivs i följande avsnitt.

## Lösning

För att åtgärda problemet måste du ange `is_filterable` (d.v.s. används i navigering i lager) och `filterable_in_search` (d.v.s. används i sökresultat med navigering i lager) till &quot;0&quot; (används inte). Gör så här:

1. Skapa en säkerhetskopia av databasen.
1. Använd ett databasverktyg som [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin) eller öppna databasen manuellt från kommandoraden för att köra följande SQL-fråga:

   ```sql
   UPDATE catalog_eav_attribute AS cea
       INNER JOIN eav_attribute AS ea
           ON ea.attribute_id = cea.attribute_id
   SET cea.is_filterable = 0, cea.is_filterable_in_search = 0
   WHERE (cea.is_filterable = 1 OR cea.is_filterable_in_search = 1)
       AND frontend_input NOT IN ('boolean', 'multiselect', 'select', 'price');
   ```

1. Kör den fullständiga omindexeringen för katalogsökning med följande kommando:

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Rensa cachen genom att köra

   ```bash
   bin/magento cache:clean
   ```

eller i Commerce Admin under **System** > **Verktyg** > **Cachehantering**.

Nu bör du kunna utföra katalogsökningar utan problem.
