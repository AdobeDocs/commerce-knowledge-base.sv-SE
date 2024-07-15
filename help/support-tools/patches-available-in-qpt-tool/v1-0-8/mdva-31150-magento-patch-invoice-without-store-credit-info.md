---
title: 'MDVA-31150: faktura utan butikskreditinformation'
description: Korrigeringen MDVA-31150 åtgärdar ett problem där en faktura skapas utan butikskreditinformation. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8 är installerat. Observera att problemet kommer att åtgärdas i Adobe Commerce version 2.4.2.
exl-id: 70c87b67-6449-4285-9679-cca81613aa72
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-31150: faktura utan butikskreditinformation

Korrigeringen MDVA-31150 åtgärdar ett problem där en faktura skapas utan butikskreditinformation. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8 har installerats. Observera att problemet kommer att åtgärdas i Adobe Commerce version 2.4.2.

## Berörda produkter och versioner

* Den här korrigeringen har utformats för Adobe Commerce i molninfrastruktur 2.3.5-p2.
* Korrigeringen är även kompatibel med Adobe Commerce lokalt och Adobe Commerce i molninfrastrukturen 2.3.0 till 2.3.5-p2 och 2.4.0 till 2.4.0-p1.

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Efter fakturabeställningen av API finns inte information om använt kundsaldo och presentkort i fakturan.

<u>Steg som ska återskapas</u>

1. Lägg till ett butikskreditbelopp till ett kundkonto: Gå till **Kunder** > **Alla kunder på sidofältet Admin.**
1. Hitta kundposten och klicka på **Redigera** i åtgärdskolumnen och sedan på **Lagra kredit** > Uppdatera saldot > **Spara kund**.
1. Gå till Storefront och lägg till produkter i kundvagnen.
1. Gör en beställning genom att tillämpa butikskrediten eller presentkortsbeloppet som en delbetalning.
1. Skapa faktura med `REST API>POST>/rest/V1/order/1/invoice` med nyttolast:    ```    { "capture": true, "items": [ { "extension_attributes": {}, "order_item_id": 3, "qty": 1 } ], "notify": true, "appendComment": true, "comment": { "extension_attributes": {}, "comment": "string", "is_visible_on_front": 0 }, "arguments": { "extension_attributes": {} }}    ```
1. Hämta fakturan som skapades med `REST API>GET>/rest/V1/invoices/1`.

<u>Förväntat resultat</u>

Butikskrediter och presentkortssaldo returneras av API Call.

<u>Faktiskt resultat</u>

Butikskrediter och presentkortssaldo returneras inte av API Call.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
