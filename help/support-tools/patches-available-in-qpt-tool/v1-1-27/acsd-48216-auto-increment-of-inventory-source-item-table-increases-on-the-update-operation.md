---
title: 'ACSD-48216: *AUTO_INCREMENT of layer_source_item* table increase on *UPDATE* operation'
description: Använd patchen ACSD-48216 för att åtgärda Adobe Commerce-problemet där *AUTO_INCREMENT för tabellen layer_source_item* ökar med åtgärden *UPDATE*.
exl-id: fb97f240-95c0-479e-ac5a-00f6792374ab
feature: Admin Workspace, Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-48216: *AUTO_INCREMENT* av *lager_källa_artikel* tabellökningar på *UPPDATERA* operation

Korrigeringen ACSD-48216 åtgärdar ett problem där *AUTO_INCREMENT* i *lager_källa_artikel* tabellökningar på *UPPDATERA* operation. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 är installerat. Korrigerings-ID är ACSD-48216. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

*AUTO_INCREMENT* i *lager_källa_artikel* tabellökningar på *UPPDATERA* operation.

<u>Steg som ska återskapas</u>:

1. Kontrollera aktuellt värde för *AUTO_INCREMENT* i *lager_källa_artikel* tabell:

```bash
MySQL > show create table inventory_source_item;
```

```SQL
CREATE TABLE `inventory_source_item` (
  `source_item_id` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `source_code` varchar(255) NOT NULL,
  `sku` varchar(64) NOT NULL,
  `quantity` decimal(12,4) NOT NULL DEFAULT '0.0000',
  `status` smallint(5) unsigned NOT NULL DEFAULT '0',
  PRIMARY KEY (`source_item_id`),
  UNIQUE KEY `INVENTORY_SOURCE_ITEM_SOURCE_CODE_SKU` (`source_code`,`sku`),
  KEY `INVENTORY_SOURCE_ITEM_SKU_SOURCE_CODE_QUANTITY` (`sku`,`source_code`,`quantity`),
  CONSTRAINT `INVENTORY_SOURCE_ITEM_SOURCE_CODE_INVENTORY_SOURCE_SOURCE_CODE` FOREIGN KEY (`source_code`) REFERENCES `inventory_source` (`source_code`) ON DELETE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=2048 DEFAULT CHARSET=utf8
```

1. Gör en API-begäran för en viss produkt:

`Endpoint: /rest/V1/inventory/source-items`\
`Method: POST`\
`Headers: Authorization: Bearer <admin_token>`

Nyttolast:

```JSON
{
    "sourceItems": [
        {
            "sku": "24-MB01",
            "source_code": "default",
            "quantity": 200,
            "status": 1
        }
    ]
}
```

1. Kontrollera *AUTO_INCREMENT* värdet på *lager_källa_artikel* tabellen igen.

<u>Förväntade resultat</u>:

The *AUTO_INCREMENT* värdet på *lager_källa_artikel* tabellen ökar inte efter varje uppdateringsåtgärd.

<u>Faktiska resultat</u>:

The *AUTO_INCREMENT* värdet på *lager_källa_artikel* tabellen ökar efter varje uppdateringsåtgärd.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
