---
title: Adobe Commerce-databasens numeriska värde ligger utanför intervallet, "INT" till "BIGINT"
description: I den här artikeln finns lösningar för när du inte kan spara en produktuppdatering, som en prisändring, eller ta bort eller duplicera en produkt.
exl-id: e2a00371-9032-4e81-b60e-5456ba35be94
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Adobe Commerce-databasens numeriska värde ligger utanför intervallet, `INT` till `BIGINT`

>[!WARNING]
>
>Innan lösningen implementeras i den här artikeln (`INT` till `BIGINT` schemauppdatering) måste alltid kontrollera att fältet som de ska ändra INTE har några relationer med främmande nycklar till en annan tabell. Om fältet har sekundärnyckelrelationer till en annan tabell uppstår problem eftersom det relaterade fältet fortfarande är `INT`. De kan använda följande fråga för att verifiera detta. Den här frågan visar vilka sekundärnyckelrelationer som är tillgängliga i databasen för det angivna tabellfältet:
>
```mysql
>SELECT 
>     TABLE_NAME,COLUMN_NAME,CONSTRAINT_NAME,REFERENCED_TABLE_NAME,REFERENCED_COLUMN_NAME
>FROM
>   INFORMATION_SCHEMA.KEY_COLUMN_USAGE
>WHERE
>     REFERENCED_TABLE_SCHEMA = '<database_name>' AND
>     REFERENCED_TABLE_NAME = '<table_name>' AND
>     REFERENCED_COLUMN_NAME = '<table_field>';
>```

## Berörda produkter och versioner

* Adobe Commerce (alla distributionsmetoder) alla [versionerna](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

I den här artikeln finns lösningar för när du inte kan spara en produktuppdatering, som en prisändring, eller ta bort eller duplicera en produkt.
Felmeddelandet kan visas *Det gick inte att spara arkivobjektet. Försök igen.* Du kanske inte kan distribuera efter en produktuppdatering. Du kan även se följande felmeddelande i MySQL när du kör `php bin/magento setup:upgrade` (i Adobe Commerce om molninfrastruktur visas det här felet i distributionsloggarna):

```mysql
SQLSTATE[22003]: Numeric value out of range: 167 Out of range value for column 'value_id' at row 1, query was: INSERT INTO `catalog_product_entity_decimal` (`attribute_id`,`store_id`,`row_id`,`value`) VALUES (?, ?, ?, ?) ON DUPLICATE KEY UPDATE `attribute_id` = VALUES(`attribute_id`), `store_id` = VALUES(`store_id`), `row_id` = VALUES(`row_id`), `value` = VALUES(`value`)
```

De lösningar som beskrivs i artikeln är:
* Uppdatera `[ AUTO_INCREMENT ]` till nästa värde från tabellen eller
* `INT` till `BIGINT` schemauppdatering

Vilken lösning du använder beror på vad som har orsakat problemet. Se stegen nedan för att isolera orsaken.

## Steg för att kontrollera orsaken


Kontrollera det högsta värdet för primärnyckeln genom att köra följande kommando i terminalen: `SELECT MAX(value_id) FROM catalog_product_entity_int;`

Om `max(value_id)` är lägre än `max int(11) [ 4294967296 ]`och `[ AUTO_INCREMENT ]` har ett värde större än eller lika med `max int(11) [ 4294967296 ]`och sedan överväga [uppdatera `[ AUTO_INCREMENT ]` till nästa värde från tabellen](#update-the-auto-increment-to-the-next-value-from-the-table). I annat fall bör du överväga en [`INT` till `BIGINT` schemauppdatering](#int_to_bigint_schema_update).

## Uppdatera `AUTO_INCREMENT` till nästa värde från tabellen {#update-the-auto-increment-to-the-next-value-from-the-table}

>[!WARNING]
>
>Säkerhetskopiera databasen innan du ändrar tabellerna. Placera webbplatsen i [underhållsläge](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode). Du bör även köra MYSQL-kommandot optimize i databastabellerna (endast i tabeller där ändringar har gjorts) efter att du har gjort ändringarna.

>[!NOTE]
>
>Platsen ska vara i underhållsläge när optimeringskommandot körs på specifika tabeller. Detta innebär att tabeller byggs om helt och hållet och att det frigörs utrymme när data har tagits bort från tabeller.

Om det visade värdet är lägre än `max int(11) [ 4294967296 ]` som visas i exemplet nedan, terminalutdata, än en tabell `[ AUTO_INCREMENT ]` har ändrats till ett tal som är större eller lika med `max [ int(11) ]` värde.

```mariadb
MariaDB [xxx]> SELECT MAX(value_id) FROM catalog_product_entity_int;
+---------------------+
| MAX(source_item_id) |
+---------------------+
|          4283174130 |
+---------------------+
```

Kör följande kommando i terminalen för att kontrollera om detta har inträffat:

```
MariaDB [xxx]> show create table catalog_product_entity_int;

...
) ENGINE=InnoDB AUTO_INCREMENT=4294967297 DEFAULT CHARSET=utf8 COMMENT='Catalog Product Integer Attribute Backend Table';
```

Som du kan se i exemplet ovan genereras tabellen `[ AUTO_INCREMENT ]` har ändrats till ett större tal än `max int(11) [ 4294967296 ]`. Lösningen är att uppdatera `[ AUTO_INCREMENT]` till nästa värde från tabellen:

```
ALTER TABLE catalog_product_entity_int AUTO_INCREMENT = 4283174131;
```

## `INT` till `BIGINT` schemauppdatering {#int_to_bigint_schema_update}

Om följande fråga körs `SELECT MAX(value_id) FROM catalog_product_entity_int;` värdet som visas är högre än `max int(11) [ 4294967296 ]`  överväga att `INT` till `BIGINT` schemauppdatering. Datatypen `BIGINT` har ett större värdeintervall.

Så här gör du:

1. Skapa en anpassad modul i *app/kod/* katalog.
1. Skapa en *db_schema.xml*. I *db_schema.xml* du ställer in datatypen på `BIGINT`.
1. Lägg till följande innehåll och kör sedan `bin/magento setup:upgrade` om du vill tillämpa ändringarna ovan på motsvarande tabell.

```
<?xml version="1.0"?>
<schema xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Setup/Declaration/Schema/etc/schema.xsd">
    <table name="catalog_product_entity_int">
        <column xsi:type="bigint" name="value_id" unsigned="false" nullable="false" identity="true"
                comment="Value ID"/>
    </table>
</schema>
```


## Relaterad läsning

* [Allmänna riktlinjer för MySQL](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql.html) i Commerce installationshandbok.
* [Databasöverföringen förlorar anslutningen till MySQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/database-upload-loses-connection-to-mysql.html) i vår kunskapsbas för support.
* [Bästa databaspraxis för Adobe Commerce om molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/database-best-practices-for-magento-commerce-cloud.html) i vår kunskapsbas för support.
* [De vanligaste databasproblemen i Adobe Commerce om molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/most-common-database-issues-in-magento-commerce-cloud.html) i vår kunskapsbas för support.
