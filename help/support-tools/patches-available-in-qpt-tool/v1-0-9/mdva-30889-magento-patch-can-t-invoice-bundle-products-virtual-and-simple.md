---
title: "MDVA-30889: Kan inte fakturera paketprodukter virtuellt och enkelt"
description: MDVA-30889-korrigeringen löser problemet där ett fel inträffar efter att en paketprodukt med både virtuella och enkla alternativ har fakturerats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: 7e6555c5-9088-4c85-920d-20c841ad6675
feature: Invoices, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-30889: Kan inte fakturera paketprodukter virtuellt och enkelt

MDVA-30889-korrigeringen löser problemet där ett fel inträffar efter att en paketprodukt med både virtuella och enkla alternativ har fakturerats. Den här korrigeringen är tillgänglig när [QPT-verktyget ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.3.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Förutsättningar</u>:

Installera Adobe Commerce med [Inventory management](https://devdocs.magento.com/guides/v2.4/inventory/).

<u>Steg som ska återskapas</u>:

1. Gå till **Admin**.
1. Skapa en enkel produkt.
1. Skapa en virtuell produkt.
1. Skapa en paketprodukt (Skapa två alternativ för underordnade produkter och tilldela virtuella och enkla produkter.) Ange **dynamiskt pris** = *Nej*.
1. Gå till butiken.
1. Gå till produktsidan.
1. Lägg produkten i kundvagnen.
1. Gå till kassan och beställ produkten.
1. Gå till **Admin > Beställningar**.
1. Öppna den skapade ordern och fakturera den.

<u>Förväntade resultat</u>:

Fakturan för en paketprodukt (som innehåller både enkla och virtuella produkter) skapas.

<u>Faktiska resultat</u>:

Fakturan skapas inte och du får ett fel som liknar detta:

```php
TypeError: Return value of Magento\InventorySourceSelection\Model\Request\InventoryRequest::getItems() must be of the type array, null returned in vendor/magento/module-inventory-source-selection/Model/Request/InventoryRequest.php:102
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
