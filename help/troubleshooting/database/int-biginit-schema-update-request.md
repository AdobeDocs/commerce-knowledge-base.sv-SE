---
title: Adobe Commerce-databasens numeriska värde ligger utanför intervallet, "INT" till "BIGINT"
description: I den här artikeln finns lösningar för när du inte kan spara en produktuppdatering, som en prisändring, eller ta bort eller duplicera en produkt.
exl-id: e2a00371-9032-4e81-b60e-5456ba35be94
feature: Services
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---

# Adobe Commerce-databasens numeriska värde ligger utanför intervallet, `INT` till `BIGINT`

>[!WARNING]
>
>Innan marknadsförare implementerar lösningen i den här artikeln (`INT` till `BIGINT` schemauppdatering) måste de alltid kontrollera att fältet som de ska ändra inte har några relationer med främmande nycklar till en annan tabell. Om fältet har sekundärnyckelrelationer till en annan tabell uppstår problem eftersom det relaterade fältet fortfarande är `INT`. De kan använda följande fråga för att verifiera detta. Den här frågan visar vilka sekundärnyckelrelationer som är tillgängliga i databasen för det angivna tabellfältet:
>
>```mysql
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

* Adobe Commerce (alla distributionsmetoder) alla [versioner som stöds](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

I den här artikeln finns lösningar för när du inte kan spara en produktuppdatering, som en prisändring, eller ta bort eller duplicera en produkt.
Felmeddelandet *Det gick inte att spara arkivobjektet. Försök igen.* Du kanske inte kan distribuera efter en produktuppdatering. Du kan även se följande [!DNL MySQL]-felmeddelande när du kör `php bin/magento setup:upgrade` (i Adobe Commerce i molninfrastruktur visas det här felet i distributionsloggarna):

```mysql
SQLSTATE[22003]: Numeric value out of range: 167 Out of range value for column 'value_id' at row 1, query was: INSERT INTO `catalog_product_entity_decimal` (`attribute_id`,`store_id`,`row_id`,`value`) VALUES (?, ?, ?, ?) ON DUPLICATE KEY UPDATE `attribute_id` = VALUES(`attribute_id`), `store_id` = VALUES(`store_id`), `row_id` = VALUES(`row_id`), `value` = VALUES(`value`)
```

De lösningar som beskrivs i artikeln är:
* Uppdatera `[ AUTO_INCREMENT ]` till nästa värde från tabellen eller
* `INT` till `BIGINT` schemauppdatering

Vilken lösning du använder beror på vad som har orsakat problemet. Se stegen nedan för att isolera orsaken.

## Steg för att kontrollera orsaken


Kontrollera det högsta värdet för primärnyckeln genom att köra följande kommando i terminalen: `SELECT MAX(value_id) FROM catalog_product_entity_int;`

Om `max(value_id)` är lägre än `max int(11) [ 4294967296 ]` och `[ AUTO_INCREMENT ]` har ett värde som är större än eller lika med `max int(11) [ 4294967296 ]`, kan du överväga att [uppdatera `[ AUTO_INCREMENT ]` till nästa värde från tabellen](#update-the-auto-increment-to-the-next-value-from-the-table). Annars bör du överväga en [`INT` till `BIGINT` schemauppdatering ](#int_to_bigint_schema_update).

## Uppdatera `AUTO_INCREMENT` till nästa värde från tabellen {#update-the-auto-increment-to-the-next-value-from-the-table}

>[!WARNING]
>
>Säkerhetskopiera databasen innan du ändrar tabellerna. Placera webbplatsen i [underhållsläge](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode). Vi rekommenderar även att du kör optimeringskommandot [!DNL MySQL] i databastabellerna (endast i tabeller där ändringar har gjorts) efter att du har gjort ändringarna.

>[!NOTE]
>
>Platsen ska vara i underhållsläge när optimeringskommandot körs på specifika tabeller. Detta innebär att tabeller byggs om helt och hållet och att det frigörs utrymme när data har tagits bort från tabeller.

Om värdet som visas är lägre än `max int(11) [ 4294967296 ]`, vilket visas i nedanstående exempel på terminalutdata, har tabellen `[ AUTO_INCREMENT ]` ändrats till ett tal som är större eller lika med värdet `max [ int(11) ]`.

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

Som du kan se i exemplet ovan har tabellen `[ AUTO_INCREMENT ]` ändrats till ett större tal än `max int(11) [ 4294967296 ]`. Lösningen är att uppdatera `[ AUTO_INCREMENT]` till nästa värde från tabellen:

```
ALTER TABLE catalog_product_entity_int AUTO_INCREMENT = 4283174131;
```

## `INT` till `BIGINT` schemauppdatering {#int_to_bigint_schema_update}

Om värdet som visas är högre än `max int(11) [ 4294967296 ]` när du kör följande fråga `SELECT MAX(value_id) FROM catalog_product_entity_int;` kan du överväga att göra en `INT` till `BIGINT`-schemauppdatering. Datatypen `BIGINT` har ett större värdeintervall.

Så här gör du:

1. Skapa en anpassad modul i katalogen *app/code/*.
1. Skapa en *db_schema.xml* i den anpassade modulen. I *db_schema.xml* anger du datatypen till `BIGINT`.
1. Lägg till följande innehåll och kör sedan `bin/magento setup:upgrade` för att tillämpa ändringarna ovan på motsvarande tabell.

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

* [Allmänna [!DNL MySQL] riktlinjer](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql.html) i Commerce installationshandbok
* [Databasöverföringen förlorar anslutningen till  [!DNL MySQL]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/database-upload-loses-connection-to-mysql.html) i vår kunskapsbas för support
* [Bästa databaspraxis för Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/database-best-practices-for-magento-commerce-cloud.html) i vår kunskapsbas för support
* [De vanligaste databasproblemen i Adobe Commerce i molninfrastrukturen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/most-common-database-issues-in-magento-commerce-cloud.html) i vår kunskapsbas för support
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
