---
title: "MDVA-35984: Fel produktkvantitet i samtidiga leveranser för samma produkt"
description: MDVA-35984-korrigeringen åtgärdar problemet när flera samtidiga leveranser skapas för samma produkt, vilket ger en felaktig produktkvantitet (kvantitet). Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 är installerat. Patch-ID:t är MDVA-35984. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.
exl-id: b15e25e1-c451-4350-950d-ae4893835e54
feature: Orders, Products, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# MDVA-35984: Fel produktkvantitet i samtidiga leveranser för samma produkt

MDVA-35984-korrigeringen åtgärdar problemet när flera samtidiga leveranser skapas för samma produkt, vilket ger en felaktig produktkvantitet (kvantitet). Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 är installerat. Patch-ID:t är MDVA-35984. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce i molninfrastruktur 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.0-2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt med **Antal** = *100*.
1. Skapa två beställningar med den här produkten.
1. Gör samtidiga API-anrop för att skapa leveranser för båda beställningarna, som i följande exempel:

   ```php
   POST <host>/rest/<store_code>/V1/order/3/ship    ```    where **order id** = *3* , with a payload like:    ```php    {        "items": [            {                "order_item_id": <order_item_id>,                "qty": 1            }        ],        "tracks": [            {                "track_number": "1Y-9876543210",                "title": "United Parcel Service",                "carrier_code": "ups"            }        ]    }
   ```

1. Kontrollera produktkvantiteten i administratörsrutnätet.

<u>Förväntade resultat</u>:

Resultatet är produkt **Kvantitet** = *98* efter båda försändelserna.

<u>Faktiska resultat</u>:

Resultatet är produkt **Kvantitet** = *99* efter båda försändelserna.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
