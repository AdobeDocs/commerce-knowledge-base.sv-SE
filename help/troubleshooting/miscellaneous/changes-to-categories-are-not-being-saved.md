---
title: Ändringar av kategorier sparas inte
description: I den här artikeln finns en fix som du kan använda när du uppdaterar produktkategorier via Commerce Admin. Ändringarna visas inte i Admin och Store. Problemet orsakas av skadade data i tabellen "catalog_category_entity". Åtgärda eller ta bort de problematiska kategoriuppdateringsposterna i tabellen för att lösa problemet. Efter det bör du kunna uppdatera produktkategorier med hjälp av Admin.
exl-id: d951205c-add9-478c-9c7d-2ba975d53b14
feature: Categories
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 0%

---

# Ändringar av kategorier sparas inte

I den här artikeln finns en fix som du kan använda när du uppdaterar produktkategorier via Commerce Admin. Ändringarna visas inte i Admin och Store. Problemet orsakas av skadade data i `catalog_category_entity` tabell. Åtgärda eller ta bort de problematiska kategoriuppdateringsposterna i tabellen för att lösa problemet. Efter det bör du kunna uppdatera produktkategorier med hjälp av Admin.

## Problem

När du har gjort ändringar i en produktkategori i Admin och sparat kommer de nya uppdateringarna varken att sparas eller visas i Admin och Store.

### Steg som ska återskapas

1. Gå till **Katalog** > **Kategorier**.
1. Välj en kategori.
1. Gör ändringarna och klicka sedan på **Spara**.
1. Meddelandet visas: *Du sparade kategorin*.
1. Observera att den ändring du har gjort inte har sparats.

## Möjlig orsak: skadade data i `catalog_category_entity` table

Problemet orsakas av samma värden i `created_in` -kolumnen för de berörda kategoriposterna i databasen (DB).

![Skadade data i tabellen catalog_category_entity](assets/catalog_category_entity.png)

Information:

* The `catalog_category_entity` Databastabellen har två eller flera poster för den berörda kategorin (dessa poster har samma `entity_id` värde).
* Dessa kategoriposter har **samma värden i `created_in` kolumn**.

### Hur visas den andra DB-posten (och alla de efterföljande) i DB för en och samma kategori?

Den andra DB-posten (och eventuellt de nästa) för den berörda kategorin innebär att det har planerats kategoriuppdateringar med modulen Magento\_Staging. Modulen skapar en extra post för en kategori i `catalog_category_entity` och det är det förväntade programbeteendet. Problemet är att posterna har samma värden för `created_in` kolumn.

### Hur visas samma värden?

Vi kan inte med säkerhet ange orsakerna till korrupta data. Möjliga orsaker kan vara:

* anpassningar (kod, teman osv.)
* felaktig datamigrering
* felaktig dataåterställning från säkerhetskopia

Så vitt vi vet är sådana datafel inte typiska för den&quot;rena&quot; (körklara) Adobe Commerce-instansen och kan inte reproduceras i en Adobe Commerce-installation utan anpassningar.

### Hur du verifierar att detta är ditt problem

The `catalog_category_entity` tabellen ska ha flera poster för den berörda kategorin (posterna ska ha samma `entity_id` värde) och minst två av posterna ska ha samma `created_in` värden. I och med detta visas inte de mellanliggande schemalagda uppdateringarna i Commerce Admin. Du ser bara det tomma blocket för schemalagda ändringar.

#### Steg som ska verifieras

1. Öppna tabellen catalog\_category\_entity i databasen.
1. Filtrera entiteter efter entitet\_id, med entiteten\_id som identifierar den berörda kategorin.
1. Om värdena i den skapade kolumnen är desamma för olika poster med samma enhet\_id är det vårt fall. Normalt visas `created_in` värdena är olika för varje post.

![Skadade data i tabellen catalog_category_entity](assets/catalog_category_entity.png)

## Lösning

Du kan välja någon av följande lösningar:

1. **Ta bort** problematiska kategoriuppdateringsposter
1. **Reparera** problematiska kategoriuppdateringsposter

### Ta bort poster för problematisk kategoriuppdatering

I den här lösningen måste du ställa in rätt `updated_in` värdet för den ursprungliga kategoriposten och ta bort alla andra poster för den här kategorin. Detta tar bort alla schemalagda kategoriuppdateringar.

Följ de här stegen:

1. Sök efter DB-poster med `entity_id` av den berörda kategorin.
1. Markera posten med det största heltalet i `updated_in` kolumn.
1. Kopiera `updated_in` värdet från den markerade posten.
1. Markera posten med `row_id` = `entity_id` (ursprunglig kategoripost) och klistra in det kopierade värdet i `updated_in` kolumn för den här posten.
1. Ta bort rad(er) med `row_id` inte lika med `entity_id` .

### Reparera de problematiska posterna för kategoriuppdatering

1. Hitta kategoriposterna med samma `entity_id` och samma `created_in` värde.
1. Välj den post där `row_id` = `entity_id` och kopiera `updated_in` värde.
1. Välj den post där `row_id` är inte lika med `entity_id` och klistra in kopierade `updated_in` värdet som `created_in` värde. Se skärmbilden nedan som en illustration.    ![Kopierar värdet created_in.png](assets/copy_created-in_value.png)
1. Verifiera att kategoriuppdateringsposten `created_in` värdet som du har uppdaterat (i steg 3) finns i `staging_update` tabell. *Till exempel:* IF kopierad `created_in` värdet är 1509281953, SEDAN enheten med `row_id` = 1509281953 måste finnas i `staging_update` table
