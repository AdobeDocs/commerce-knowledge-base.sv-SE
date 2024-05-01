---
title: 'MDVA-28763: problem med att hantera produktbilder via REST API'
description: MDVA-28763-korrigeringen åtgärdar flera problem som rör hantering av mediegalleriet med REST API. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 är installerat. Problemen är schemalagda att åtgärdas i senare versioner av Adobe Commerce.
exl-id: 736fbfa8-b6a3-413c-a220-fd772d87ed04
feature: REST, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MDVA-28763: problem med att hantera produktbilder via REST API

MDVA-28763-korrigeringen åtgärdar flera problem som rör hantering av mediegalleriet med REST API. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 är installerat. Problemen är schemalagda att åtgärdas i senare versioner av Adobe Commerce (se felbeskrivningar i [Problem](#issues).

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce lokal 2.3.2 - 2.3.3.x
* Adobe Commerce i molninfrastruktur 2.3.2 - 2.3.3.x

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem {#issues}

MDVA-28763-korrigeringen innehåller korrigeringar för följande problem som är kopplade till mediegalleriet:

* När REST API används för att uppdatera YouTube-videofilmer (`PUT rest/V1/products/ {SKU}`I visas en miniatyrbild för videon, men videospelaren läses inte in när du klickar på knappen Spela upp. Planerad att åtgärdas i Adobe Commerce 2.3.6.
* `PUT /V1/products/:sku/media/:entryId` anrop skapar en ny post i stället för att ersätta den befintliga. Fixed in Adobe Commerce 2.3.5.
* Problem med borttagning av produktbilder när produkter tilldelas flera butiksvyer. Fixed in Adobe Commerce 2.3.4.
* Merchants med flera webbplatser kan nu använda REST för att skapa och uppdatera produkter samtidigt som arvet av bild och roll bevaras. Tidigare, när en handlare använde REST för att skapa och uppdatera produkter och en produkt uppdaterades för butiksvyn, lästes standardrollerna in och sparades för butiksvyn. Därför slutade rollerna för butiksvisningsbilder att ärva från standardomfånget efter uppdateringen. Planerad att åtgärdas i Adobe Commerce 2.3.6.
* Medieattribut (bild, miniatyrbild, ...) värden i butiksvyer som refererar till borttagna bilder som inte rensas automatiskt. Planerad att åtgärdas i Adobe Commerce 2.4.2.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
