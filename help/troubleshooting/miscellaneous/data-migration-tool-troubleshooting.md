---
title: Felsökning av datamigreringsverktyget
description: Den här artikeln innehåller lösningar på fel som kan uppstå när du kör datamigreringsverktyget.
exl-id: 9beb31ae-ed3c-42e1-b0bf-33fb1c91e0ea
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# Felsökning av datamigreringsverktyget

Den här artikeln innehåller lösningar på fel som kan uppstå när du kör datamigreringsverktyget.

## Källdokument/fält är inte mappade {#source-documents-fields-not-mapped}

### Felmeddelanden

* ```bash    Source documents are not mapped: <EXTENSION_TABLE>    ```
* ```bash    Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <EXTENSION_FIELD>    ```

I sällsynta fall kan meddelandet nämna

```bash
Destination documents
```

eller

```bash
Destination fields
```

i stället för källfiler.

### Orsak

Vissa Adobe Commerce version 1-enheter (som i de flesta fall kommer från tillägg) finns inte i Adobe Commerce version 2-databasen.

Det här meddelandet visas eftersom datamigreringsverktyget kör interna tester för att verifiera att tabeller och fält är konsekventa mellan *källa* (Adobe Commerce 1) och *mål* (Adobe Commerce 2) databaser.

### Möjliga lösningar

* Installera motsvarande Adobe Commerce 2-tillägg från [Commerce Marketplace](https://marketplace.magento.com/).     Om data som är i konflikt härstammar från ett tillägg som lägger till egna databasstrukturelement, kan Adobe Commerce 2-versionen av samma tillägg lägga till sådana element i måldatabasen (Adobe Commerce 2) och på så sätt åtgärda problemet.
* Använd `-a` -argument när verktyget körs för att automatiskt lösa fel och förhindra att migreringen stoppas.
* Konfigurera verktyget för att ignorera problematiska data.

Om du vill ignorera databasenheter lägger du till `<ignore>` tagga till en enhet i `map.xml` så här:

```xml
...
    <source>
        <document_rules>
            ...
            <!-- Ignore `sales_flat_invoice_grid` table -->
            <ignore>
                <document>sales_flat_invoice_grid</document>
            </ignore>
            <!-- Ignore `address_id` field of `sales_flat_order_address` table -->
            <ignore>
                <field>sales_flat_order_address.address_id</field>
            </ignore>
            ...
        </document_rules>
    </source>
    ...
```

>[!WARNING]
>
>Innan du ignorerar enheter med hjälp av mappningsfilen eller `-a` måste du se till att du inte behöver data som påverkas i din Adobe Commerce 2 Store.

## Klassen har inte mappats i posten {#class-does-not-exist-but-mentioned}

### Felmeddelande

```bash
Class <extension/class_name> is not mapped in record <attribute_id=196>
```

### Orsak

Det gick inte att hitta en klass från Adobe Commerce 1 i Adobe Commerce 2-kodbasen under [EAV-migreringssteg](https://devdocs.magento.com/guides/v2.3/migration/migration-tool-internal-spec.html#eav) i vår dokumentation för utvecklare. I de flesta fall tillhör den klass som saknas en [extension](https://glossary.magento.com/extension).

### Möjliga lösningar

* Installera motsvarande Adobe Commerce 2-tillägg.
* Ignorera attributet som orsakar problemet.    Lägg till attributet i `ignore` grupp i `eav-attribute-groups.xml.dist` -fil.
* Lägg till klassmappning med `class-map.xml.dist` -fil.

## Sekundärnyckelbegränsningen misslyckades

### Felmeddelandetext

```bash
Foreign key <KEY_NAME> constraint fails on source database. Orphan records id: <id_1>, <id_2> from <child_table>.<field_id> has no referenced records in <parent_table>
```

### Orsak

Det saknas databasposter i `parent_table` till vilken `field_id` i `child_table` pekar på.

### Möjlig lösning

Ta bort posterna från `child_table` , om du inte behöver dem.

Om du vill behålla posterna inaktiverar du `Data Integrity Step` genom att ändra datamigreringsverktygets `config.xml` .

## Dupliceringar i URL-omskrivningar

```xml
There are duplicates in URL rewrites:
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/10
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/12
```

### Orsak

The `Target path` i en URL-omskrivning måste anges med ett unikt par av `Request path` + `Store ID` . Det här felet rapporterar två poster som använder samma `Request path` + `Store ID` par med två olika `Target path` värden.

### Möjlig lösning

Aktivera `auto_resolve_urlrewrite_duplicates` i `config.xml` -fil.

Den här konfigurationen lägger till en hash-sträng i de poster i [URL](https://glossary.magento.com/url) skriver om och visar upplösningsresultatet i kommandoradsgränssnittet.

## Enheter som inte matchar {#mismatch-of-entities}

### Felmeddelande

```bash
Mismatch of entities in the document: <DOCUMENT> Source: <COUNT_ITEMS_IN_SOURCE_TABLE> Destination: <COUNT_ITEMS_IN_DESTINATION_TABLE>
```

### Orsak

Felet inträffar under volymkontrollsteget. Det innebär att antalet databasposter i Adobe Commerce 2 för dokumentet inte är detsamma som i Adobe Commerce 1.

Saknade poster inträffar när en kund gör en beställning under migreringen.

### Möjlig lösning

Kör datamigreringsverktyget i `Delta` läge för överföring av inkrementella ändringar.

## Delalog har inte installerats {#deltalog-is-not-installed}

### Felmeddelande

```bash
Deltalog for <TABLE_NAME> is not installed
```

### Orsak

Detta fel inträffar under [stegvis migrering](https://devdocs.magento.com/guides/v2.3/migration/migration-migrate-delta.html) (i vår utvecklardokumentation) om dataändringar. Det betyder deltabulationer (med prefix) `m2_cl_*`) hittades inte i Adobe Commerce 1-databasen. Verktyget installerar tabellerna under [datamigrering](https://devdocs.magento.com/guides/v2.3/migration/migration-migrate-data.html) (i vår dokumentation för utvecklare) liksom databasutlösare som spårar ändringar och fyller i tabeller för beskrivningar.

En orsak till felet kan vara att du försöker migrera från en *copy* i Adobe Commerce 1-butiken, inte i själva butiken. När du gör en kopia från en Adobe Commerce 1-butik som aldrig har migrerats innehåller kopian inte de utlösare och ytterligare delatabeller som behövs för att slutföra en deltamigrering, så migreringen misslyckas. Datamigreringsverktyget gör INTE jämförelser mellan databasen för AC1 och AC2 för att migrera skillnaderna. Verktyget använder i stället de utlösare och delatogtabeller som installerats under den första migreringen för att utföra efterföljande deltmigreringar. I så fall kommer ditt exemplar av Adobe Commerce 1 DB inte att innehålla de utlösare och delatabeller som datamigreringsverktyget använder för att utföra en migrering.

### Möjlig lösning

Vi rekommenderar att du testar migreringsprocessen från en kopia av din Adobe Commerce 1-databas för att åtgärda dina migreringsproblem. När du har åtgärdat problemen i kopian startar du om migreringsprocessen från Adobe Commerce 1-databasen. Detta bidrar till att säkerställa en smidig migreringsprocess.
