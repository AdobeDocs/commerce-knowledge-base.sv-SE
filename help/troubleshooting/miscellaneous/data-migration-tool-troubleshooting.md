---
title: Felsökning av datamigreringsverktyget
description: Den här artikeln innehåller lösningar på fel som kan uppstå när du kör datamigreringsverktyget.
exl-id: 9beb31ae-ed3c-42e1-b0bf-33fb1c91e0ea
feature: Data Import/Export
role: Developer
source-git-commit: 958067830d32b1f10ffa669307ec76d1e14b82a4
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Felsökning av datamigreringsverktyget

Den här artikeln innehåller lösningar på fel som kan uppstå när du kör datamigreringsverktyget.

## Source-dokument/fält är inte mappade {#source-documents-fields-not-mapped}

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

Det här meddelandet visas eftersom datamigreringsverktyget kör interna tester för att verifiera att tabeller och fält är konsekventa mellan databaserna *source* (Adobe Commerce 1) och *destination* (Adobe Commerce 2).

### Möjliga lösningar

* Installera motsvarande Adobe Commerce 2-tillägg från [Commerce Marketplace](https://marketplace.magento.com/).     Om data som är i konflikt härstammar från ett tillägg som lägger till egna databasstrukturelement, kan Adobe Commerce 2-versionen av samma tillägg lägga till sådana element i måldatabasen (Adobe Commerce 2) och på så sätt åtgärda problemet.
* Använd argumentet `-a` när du kör verktyget för att lösa fel automatiskt och förhindra att migreringen stoppas.
* Konfigurera verktyget för att ignorera problematiska data.

Om du vill ignorera databasentiteter lägger du till taggen `<ignore>` i en entitet i filen `map.xml` enligt följande:

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
>Innan du ignorerar entiteter efter mappningsfil eller använder alternativet `-a` måste du se till att du inte behöver de data som påverkas i Adobe Commerce 2 Store.

## Klassen har inte mappats i posten {#class-does-not-exist-but-mentioned}

### Felmeddelande

```bash
Class <extension/class_name> is not mapped in record <attribute_id=196>
```

### Orsak

Det gick inte att hitta en klass från Adobe Commerce 1-kodbasen i Adobe Commerce 2 under migreringssteget [EAV](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/data-migration/basics/technical-specification) i utvecklardokumentationen. I de flesta fall tillhör den klass som saknas ett [tillägg](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/glossary#extension).

### Möjliga lösningar

* Installera motsvarande Adobe Commerce 2-tillägg.
* Ignorera attributet som orsakar problemet.    För detta lägger du till attributet i gruppen `ignore` i filen `eav-attribute-groups.xml.dist`.
* Lägg till klassmappning med filen `class-map.xml.dist`.

## Sekundärnyckelbegränsningen misslyckades

### Felmeddelandetext

```bash
Foreign key <KEY_NAME> constraint fails on source database. Orphan records id: <id_1>, <id_2> from <child_table>.<field_id> has no referenced records in <parent_table>
```

### Orsak

Det saknas databasposter i `parent_table` som `field_id` av `child_table` pekar på.

### Möjlig lösning

Ta bort posterna från `child_table` om du inte behöver dem.

Om du vill behålla posterna inaktiverar du `Data Integrity Step` genom att ändra `config.xml` för datamigreringsverktyget.

## Dupliceringar i URL-omskrivningar

```xml
There are duplicates in URL rewrites:
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/10
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/12
```

### Orsak

`Target path` i en URL-omskrivning måste anges med ett unikt par av `Request path` + `Store ID` . Det här felet rapporterar två poster som använder samma `Request path` + `Store ID`-par med två olika `Target path`-värden.

### Möjlig lösning

Aktivera alternativet `auto_resolve_urlrewrite_duplicates` i din `config.xml`-fil.

Den här konfigurationen lägger till en hash-sträng i posterna med URL-omskrivningar som står i konflikt och visar upplösningsresultatet i kommandoradsgränssnittet.

## Enheter som inte matchar {#mismatch-of-entities}

### Felmeddelande

```bash
Mismatch of entities in the document: <DOCUMENT> Source: <COUNT_ITEMS_IN_SOURCE_TABLE> Destination: <COUNT_ITEMS_IN_DESTINATION_TABLE>
```

### Orsak

Felet inträffar under volymkontrollsteget. Det innebär att antalet databasposter i Adobe Commerce 2 för dokumentet inte är detsamma som i Adobe Commerce 1.

Saknade poster inträffar när en kund gör en beställning under migreringen.

### Möjlig lösning

Kör datamigreringsverktyget i `Delta`-läge om du vill överföra inkrementella ändringar.

## Delalog har inte installerats {#deltalog-is-not-installed}

### Felmeddelande

```bash
Deltalog for <TABLE_NAME> is not installed
```

### Orsak

Det här felet inträffar under [inkrementell migrering](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/data-migration/migrate-data/delta) (i vår utvecklardokumentation) av dataändringar. Det betyder att deltabulatorer (med prefix `m2_cl_*`) inte hittades i Adobe Commerce 1-databasen. Verktyget installerar dessa tabeller under [datamigrering](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/data-migration/migrate-data/data) (i vår utvecklardokumentation) samt databasutlösare som spårar ändringar och fyller i deltabeller.

En orsak till felet kan vara att du försöker migrera från en *kopia* av din Adobe Commerce 1-butik, inte från själva livebutiken. När du gör en kopia från en Adobe Commerce 1-butik som aldrig har migrerats innehåller kopian inte de utlösare och ytterligare delatabeller som behövs för att slutföra en deltamigrering, så migreringen misslyckas. Datamigreringsverktyget gör INTE jämförelser mellan databasen för AC1 och AC2 för att migrera skillnaderna. Verktyget använder i stället de utlösare och delatogtabeller som installerats under den första migreringen för att utföra efterföljande deltmigreringar. I så fall kommer ditt exemplar av Adobe Commerce 1 DB inte att innehålla de utlösare och delatabeller som datamigreringsverktyget använder för att utföra en migrering.

### Möjlig lösning

Vi rekommenderar att du testar migreringsprocessen från en kopia av din Adobe Commerce 1-databas för att åtgärda dina migreringsproblem. När du har åtgärdat problemen i kopian startar du om migreringsprocessen från Adobe Commerce 1-databasen. Detta bidrar till att säkerställa en smidig migreringsprocess.

## Relaterad läsning

[Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook

