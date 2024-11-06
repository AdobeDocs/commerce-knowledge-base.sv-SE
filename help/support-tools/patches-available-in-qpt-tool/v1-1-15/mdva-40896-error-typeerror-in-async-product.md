---
title: '"MDVA-40896: ''Fel: TypeError: Argument 3''-fel i asynkron produkt'''
description: '"Korrigeringen MDVA-40896 åtgärdar ett fel där felet "Error: TypeError: Argument 3 som skickas till Magento\Framework\Webapi\ServiceInputProcessor::process() måste vara av typen array, strängen given" visas i asynkront produktbulk-API. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 är installerat. Korrigerings-ID är MDVA-40896. Observera att problemet har åtgärdats i Adobe Commerce 2.4.4."'
exl-id: d9b73e7a-c228-492c-9fdf-c57cceafb330
feature: Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# MDVA-40896: Fel: TypeError: Argument 3 fel i asynkron produkt

MDVA-40896-korrigeringen åtgärdar ett problem där felet `Error: TypeError: Argument 3 passed to Magento\Framework\Webapi\ServiceInputProcessor::process() must be of the type array, string given` visas i asynkront produkt-bulk-API. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 är installerat. Korrigerings-ID är MDVA-40896. Observera att problemet har åtgärdats i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

`Error: TypeError: Argument 3 passed to Magento\Framework\Webapi\ServiceInputProcessor::process() must be of the type array, string given`-fel visas i asynkront produkt-bulk-API.

<u>Steg som ska återskapas</u>:

1. Skicka en begäran till `rest/all/async/bulk/V1/products/bySKU`-slutpunkten med följande nyttolast:

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

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i vår utvecklardokumentation.
