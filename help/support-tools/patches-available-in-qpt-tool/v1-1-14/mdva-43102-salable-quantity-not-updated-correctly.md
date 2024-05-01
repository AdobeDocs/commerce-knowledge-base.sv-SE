---
title: 'MDVA-43102: Den säljbara kvantiteten har inte uppdaterats korrekt'
description: MDVA-43102-korrigeringen åtgärdar ett problem där den säljbara kvantiteten inte uppdateras korrekt när en återbetalning görs via REST API. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 är installerat. Korrigerings-ID är MDVA-43102. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: c51bc45b-a7e0-4581-a318-9c4736e6661c
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-43102: Den säljbara kvantiteten har inte uppdaterats korrekt

MDVA-43102-korrigeringen åtgärdar ett problem där den säljbara kvantiteten inte uppdateras korrekt när en återbetalning görs via REST API. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 är installerat. Korrigerings-ID är MDVA-43102. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.1 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Den säljbara kvantiteten uppdateras inte korrekt när en återbetalning görs med REST API.

<u>Steg som ska återskapas</u>:

1. Lägg en artikel i kundvagnen.
1. Kontrollera lagerkvantitet och säljbar kvantitet.
1. Skapa en order.
1. Skapa en faktura vid behov.
1. Skicka en REST-begäran om att återbetala fakturan med följande nyttolast:

   * offline-metod/order/`<order_id>`/återbetalning
   * online-metod/faktura/`<invoice_id>`/återbetalning

   ```rest
   {
     "items": [
     {
       "order_item_id": <order_item_id>,
       "qty": 1
     }
     ],
     "notify": true,
     "arguments": {
       "shipping_amount": 5,
       "extension_attributes": {
         "return_to_stock_items": [
         <order_item_id>
         ]
       }
     }
   }
   ```

1. Skicka inte objekten.
1. Jämför lagerkvantitet och försäljningskvantitet från tidigare. Båda bör uppdateras med samma belopp.

<u>Förväntade resultat</u>:

Den säljbara kvantiteten uppdateras korrekt när en återbetalning utfärdas innan ordern levereras och produkten returneras till lagret.

<u>Faktiska resultat</u>:

Den säljbara kvantiteten uppdateras inte när en återbetalning utfärdas innan ordern levereras och produkten returneras till lagret.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
