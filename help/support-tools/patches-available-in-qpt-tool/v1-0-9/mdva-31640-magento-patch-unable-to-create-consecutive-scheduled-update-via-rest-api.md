---
title: 'MDVA-31640-korrigering: Det går inte att skapa en efterföljande schemalagd uppdatering via REST API'
description: Korrigeringen MDVA-31640 åtgärdar ett problem där en ny schemalagd uppdatering för specialpriset inte kan skapas för flera butiker med hjälp av REST API, om uppdateringens startdatum sammanfaller med slutdatumet för den tidigare befintliga uppdateringen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: 8d91db3d-7c94-4757-8087-4cf53cad81e7
feature: REST
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# MDVA-31640-korrigering: Det går inte att skapa efterföljande schemalagda uppdateringar via REST API

Korrigeringen MDVA-31640 åtgärdar ett problem där en ny schemalagd uppdatering för specialpriset inte kan skapas för flera butiker med hjälp av REST API, om uppdateringens startdatum sammanfaller med slutdatumet för den tidigare befintliga uppdateringen. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen skapades för Adobe Commerce-versionen:**

Adobe Commerce om molninfrastruktur 2.3.5-p1

**Kompatibel med Adobe Commerce:**

Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.1 - 2.3.5-p2, 2.4.0, 2.4.0-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Korrigerar problemet där en ny schemalagd uppdatering för specialpriset inte kan skapas för flera butiker med REST API, om uppdateringens startdatum sammanfaller med slutdatumet för den tidigare befintliga uppdateringen.

<u>Steg som ska återskapas</u>:

1. Konfigurera ytterligare en webbplats-, butiks- och butiksvy.
1. Skapa två enkla produkter: &quot;product1&quot; och &quot;product2&quot;.
1. Tilldela produkt1 till en webbplats och produkt2 till båda webbplatserna.
1. Skapa en schemalagd uppdatering för specialpriset för produkten1 i butiksvyn för butiken med ID 1. Använd REST API `POST` begäran till `rest/V1/products/special-price` med följande nyttolast:
   `{        "prices": [            {                "price": 15,                "store_id": 1,                "sku": "product1",                "price_from": "2021-11-15 04:00:00",                "price_to": "2021-11-15 04:10:00"            }        ]    }`
1. Skapa en schemalagd uppdatering för specialpriset för produkten2 i båda butiksvyerna för butiker med ID 1 och 2 med REST API `POST` begäran till `rest/V1/products/special-price` med följande nyttolast ( `price_from` datumet är samma som `price_to` datum i föregående begäran):
   `{        "prices": [            {                "price": 14,                "store_id": 1,                "sku": "product2",                "price_from": "2021-11-15 04:10:00",                "price_to": "2021-11-15 04:15:00"            },            {                "price": 13,                "store_id": 2,                "sku": "product2",                "price_from": "2021-11-15 04:10:00",                "price_to": "2021-11-15 04:15:00"            }        ]    }`

<u>Förväntade resultat</u>:

Den schemalagda uppdateringen med specialprisändringen skapas i båda butiksvyerna.

<u>Faktiska resultat</u>:

Adobe Commerce genererar ett fel. Schemalagd uppdatering har inte skapats.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
