---
title: Produktbilder visas inte trots produktredigeringsroller
description: I den här artikeln finns en korrigering för när produktbilder inte visas i din butik, trots att bildroller har angetts på sidan för produktredigering.
exl-id: 456baa5a-fa16-4bc1-9d6c-54106fae58ca
feature: Cache, Products, Roles/Permissions, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# Produktbilder visas inte trots produktredigeringsroller

I den här artikeln finns en korrigering för när produktbilder inte visas i din butik, trots att bildroller har angetts på sidan för produktredigering.

**Orsak:** på Adobe Commerce-instanser med mer än en butik kan en del produktbilder ha `no_selection` värden för bildrollsattribut `image`, `small_image`, `thumbnail`, `swatch`. sådan `no_selection` värden uppstår när produktavbildningsrollen anges i det globala omfånget för alla butiker i stället för i en viss butiks omfång (med andra ord på **Alla butiksvyer** i stället för en viss **Butiksvy**). Om du vill veta om det är ditt fall kör du SQL-skriptet från **Orsak** nedan.

**Lösning:** ta bort rader med `no_selection` värden för sådana bilder med hjälp av SQL-skriptet från lösningsavsnittet nedan.

## Berörda versioner

* Adobe Commerce lokal 2.X.X
* Adobe Commerce i molninfrastruktur 2.X.X

## Problem

Produktbilder kanske inte visas i din butik, även om bildrollerna (Bas, Liten, Miniatyrbild, Färgruta) har angetts korrekt på sidan Produkt på panelen Admin.

När du kontrollerar produktsidan med **Butiksvy** ange till **Alla butiksvyer** har bilden de roller som är inställda på **Bilddetaljer** skärm.

![all_store_views.png](assets/all_store_views.png)

![image_roles.png](assets/image_roles.png)

I butiken visas dock inte bilden. När du kontrollerar produktsidan på den aktuella butiksnivån (byter du **Butiksvy**) finns bilden där men rollerna är inte angivna.

![image_roles_not_set.png](assets/image_roles_not_set.png)

## Orsak

I Adobe Commerce-instanser för flera butiker (med fler än en butik) kan vissa produktbilder ha `no_selection` värden för attribut `image`, `small_image`, `thumbnail`, `swatch` (dessa attribut motsvarar bildroller). sådan `no_selection` värden uppstår när produktavbildningsrollen anges i det globala omfånget för alla butiker i stället för i en viss butiks omfång (med andra ord på **Alla butiksvyer** i stället för en viss **Butiksvy**).

Tekniskt sett: på `store_id=0` (som innehåller globala inställningar för alla butiker på din Adobe Commerce-instans), kan produktavbildningsrollerna anges: det innebär att attributen `image`, `small_image`, `thumbnail`, `swatch` har giltiga värden (sökväg till bilder). Samtidigt är `store_id=1` (som är en viss butiksrepresentation) är värdena för dessa attribut `no_selection`.

### Så här kontrollerar du att det är ditt problem

Kör den här SQL-frågan:

```sql
SELECT `cpev_s`.*, `cpev_0`.`value` AS `store_value` FROM `catalog_product_entity_varchar` `cpev_s` JOIN `eav_attribute` `ea` ON `cpev_s`.`attribute_id` = `ea`.`attribute_id` LEFT JOIN `catalog_product_entity_varchar` `cpev_0` ON `cpev_0`.`row_id` = `cpev_s`.`row_id` AND `cpev_0`.`attribute_id` = `cpev_s`.`attribute_id` AND `cpev_0`.`store_id` = 0 WHERE `cpev_s`.`value` = 'no_selection' AND `ea`.`attribute_code` IN ('image', 'small_image', 'thumbnail') AND `cpev_s`.`store_id` > 0 AND `cpev_s`.`value` != `cpev_0`.`value` AND `cpev_s`.`value` = 'no_selection';
```

Om frågan returnerar ett resultat som det nedan, hanterar du problemet som beskrivs i den här artikeln:

```sql
+----------+--------------+----------+--------+--------------+----------------------------+
| value_id | attribute_id | store_id | row_id | value        | store_value                |
+----------+--------------+----------+--------+--------------+----------------------------+
|    67722 |           87 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67723 |           88 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67724 |           89 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67814 |           87 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6769 |           87 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|    67815 |           88 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6770 |           88 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|    67816 |           89 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6771 |           89 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
+----------+--------------+----------+--------+--------------+----------------------------+
9 rows in set (0.06 sec)
```

### Varför händer det här?

Om Adobe Commerce-programmet har mer än en butik kanske det inte synkroniserar data mellan en viss butik och den globala lagringsinställningarna.

Värden på `store_id=1` har högre prioritet än standardarkivet (global) (`store_id=0`). Programmet kan därför ignorera de globala bildinställningarna och använda lagringsomfångskonfigurationen (`no_selection` för bildrollsattribut) när en bild visas.

## Lösning {#solution}

Ta bort attribut med `no_selection` värden som använder detta SQL-skript:

```
DELETE `cpev_s`.* FROM `catalog_product_entity_varchar` `cpev_s` JOIN `eav_attribute` `ea` ON `cpev_s`.`attribute_id` = `ea`.`attribute_id` LEFT JOIN `catalog_product_entity_varchar` `cpev_0` ON `cpev_0`.`row_id` = `cpev_s`.`row_id` AND `cpev_0`.`attribute_id` = `cpev_s`.`attribute_id` AND `cpev_0`.`store_id` = 0 WHERE `cpev_s`.`value` = 'no_selection' AND `ea`.`attribute_code` IN ('image', 'small_image', 'thumbnail') AND `cpev_s`.`store_id` > 0 AND `cpev_s`.`value` != `cpev_0`.`value` AND `cpev_s`.`value` = 'no_selection';
```

När attributen har tagits bort ställs rollerna för vissa butiker in och bilderna visas i butiken.

## Ytterligare information

Du kommer inte att kunna se korrigeringsresultaten direkt om helsidescache är aktiverat i din Adobe Commerce-instans.

Uppdatera sidcachen med **Cachehantering** -menyn på din Admin-panel.

## Mer information

### Lager och omfång

[Lagrar och lagra omfattningar](/docs/commerce-admin/stores-sales/site-store/stores.html) i vår användarhandbok

### Bilder

[Överför produktbilder](/docs/commerce-admin/catalog/products/digital-assets/product-image.html#upload-an-image) i vår användarhandbok

### Cache

* [Cachehantering](/docs/commerce-admin/systems/tools/cache-management.html) i vår användarhandbok för Admin System.
* [Hantera cachen](/docs/commerce-operations/configuration-guide/cli/manage-cache.html) i vår utvecklardokumentation