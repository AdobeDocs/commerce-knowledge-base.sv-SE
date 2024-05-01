---
title: '"MDVA-40896: ''Fel: TypeError: Argument 3''-fel i asynkron produkt'''
description: '"Korrigeringen MDVA-40896 åtgärdar ett fel där felet "Error: TypeError: Argument 3 som skickas till Magento\Framework\Webapi\ServiceInputProcessor::process() måste vara av typen array, strängen given" visas i asynkront produktbulk-API. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 är installerat. Korrigerings-ID är MDVA-40896. Observera att problemet har åtgärdats i Adobe Commerce 2.4.4."'
exl-id: d9b73e7a-c228-492c-9fdf-c57cceafb330
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# MDVA-40896: Fel: TypeError: Argument 3 fel i asynkron produkt

MDVA-40896-korrigeringen åtgärdar problemet där `Error: TypeError: Argument 3 passed to Magento\Framework\Webapi\ServiceInputProcessor::process() must be of the type array, string given` fel visas i asynkron produktgrupp-API. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 är installerat. Korrigerings-ID är MDVA-40896. Observera att problemet har åtgärdats i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

`Error: TypeError: Argument 3 passed to Magento\Framework\Webapi\ServiceInputProcessor::process() must be of the type array, string given` fel visas i asynkron produktgrupp-API.

<u>Steg som ska återskapas</u>:

1. Skicka en förfrågan till `rest/all/async/bulk/V1/products/bySKU` slutpunkt med följande nyttolast:

```RESTAPI
[
  {
    "product": {
      "sku": "24-MB01",
      "price": 36,
      "extension_attributes": {
        "stock_item": {
          "qty": 100,
          "is_in_stock": true
        }
      },
      "custom_attributes": [
        {
          "attribute_code": "new",
          "value": "1"
        }
      ]
    }
  },
  {
    "product": {
      "sku": "24-MB04",
      "price": 28,
      "extension_attributes": {
        "stock_item": {
          "qty": 50,
          "is_in_stock": true
        }
      },
      "custom_attributes": [
        {
          "attribute_code": "new",
          "value": "0"
        }
      ]
    }
  }
]
```

<u>Förväntade resultat</u>:

Produktinformation returneras.

<u>Faktiska resultat</u>:

Felet `Error: TypeError: Argument 3 passed to Magento\Framework\Webapi\ServiceInputProcessor::process() must be of the type array, string given` inträffar.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
