---
title: 'MDVA-43102: Den säljbara kvantiteten har inte uppdaterats korrekt'
description: MDVA-43102-korrigeringen åtgärdar ett problem där den säljbara kvantiteten inte uppdateras korrekt när en återbetalning görs via REST API. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 är installerat. Korrigerings-ID är MDVA-43102. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: c51bc45b-a7e0-4581-a318-9c4736e6661c
feature: Variables
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-43102: Den säljbara kvantiteten har inte uppdaterats korrekt

MDVA-43102-korrigeringen åtgärdar ett problem där den säljbara kvantiteten inte uppdateras korrekt när en återbetalning görs via REST API. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 är installerat. Korrigerings-ID är MDVA-43102. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.1 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Den säljbara kvantiteten uppdateras inte korrekt när en återbetalning görs med REST API.

<u>Steg som ska återskapas</u>:

1. Lägg en artikel i kundvagnen.
1. Kontrollera lagerkvantitet och säljbar kvantitet.
1. Skapa en order.
1. Skapa en faktura vid behov.
1. Skicka en REST-begäran om att återbetala fakturan med följande nyttolast:

   * offline-metod/order/`<order_id>`/återbetalning
   * onlinetod/faktura/`<invoice_id>`/återbetalning

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

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i vår utvecklardokumentation.
