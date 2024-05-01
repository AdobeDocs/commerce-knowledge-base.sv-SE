---
title: Det finns flera rader i databasen för samma enhet
description: Den här artikeln innehåller en lösning på problemet där det finns flera rader för samma enhets-ID i databasen.
feature: Catalog Management, Categories, Services, Storefront
role: Developer
exl-id: 09d5c321-9c45-4041-b6f6-831efca0977e
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Flera rader i databasen för samma enhet

Den här artikeln innehåller en lösning på problemet där det finns flera rader för samma enhets-ID i databasen.

## Berörda produkter och versioner:

* Adobe Commerce (alla versioner)

## Problem

Det finns flera rader för samma enhets-ID i databasen.

När du till exempel har tagit emot en lista över poster med duplicerade enhets-ID:n när du kör den här frågan:

```
SELECT * FROM $entityTable WHERE $column = <$entityID> ORDER BY created_in;
```

Plats `$entityID = ID` av kategori/produkt/kundvagnsprisregel/katalogprisregel/CMS-sida.

| Entitet | $entityTable | $column |
|------------------|-----------------------------------|------------------|
| Kategori/produkt | catalog_category_entity/catalog_product_entity | entity_id |
| Kundprisregel/katalogprisregel | salesrule/catalogrle | rule_id |
| CMS-sida | cms_page | page_id |

## Orsak

Detta är det förväntade beteendet. De flera raderna skapas med funktionen Innehållsmellanlagring:

* Om du anger ett startdatum utan ett slutdatum kommer det att finnas minst två rader med samma enhets-/regel-/sid-ID. En rad visar enhetens ursprungliga tillstånd (den rad i vilken `created_in=1`) och en rad visar *Slut på schemalagd uppdatering*.

* Om du anger ett startdatum med ett slutdatum kommer det att finnas minst tre rader med samma enhets-/regel-/sid-ID. En rad visar enhetens ursprungliga tillstånd (den rad i vilken `created_in=1`) kommer en rad att finnas för *Start för den schemalagda uppdateringen* och en rad kommer att finnas för *Slut på schemalagd uppdatering*.

I den här frågan:

```
SELECT row_id, entity_id, created_in, updated_in FROM catalog_product_entity WHERE entity_id = 483 ORDER BY created_in;
```

![multiple_rows_in_database.png](assets/multiple_rows_in_database.png)

* The `created_in` och `updated_in` värdena ska följa detta mönster: `created_in` värdet för den aktuella raden är lika med `updated_in` värdet i föregående rad. Den första raden ska dessutom innehålla `created_in = 1` och den sista raden ska innehålla `updated_in = 2147483647`. (Om det bara finns en rad måste du se `created_in=1` och `updated_in=2147483647`).

### Varför visas den andra DB-posten (och alla de efterföljande) i DB för samma entitet?

* Den andra DB-posten (och, eventuellt, nästa) för den berörda entiteten betyder att det har planerats uppdateringar av innehållsmellanlagring med `Magento_Staging` som skapar en extra post för en enhet i respektive register.

Ett problem uppstår bara om posterna har samma värden för `created_in` eller `updated_in` kolumner.

## Lösning

Detta är det förväntade beteendet och leder bara till problem om det finns skillnader mellan raderna.

## Relaterad läsning

* [Ändringar av kategorier sparas inte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/changes-to-categories-are-not-being-saved.html) i vår kunskapsbas för support.
* [Duplicera poster i katalogtabellen efter redigering av slutdatum för en schemauppdatering](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/duplicate-entries-in-the-catalogrule-table-after-editing-the-end-date-of-a-schedule-update.html) i vår kunskapsbas för support.
