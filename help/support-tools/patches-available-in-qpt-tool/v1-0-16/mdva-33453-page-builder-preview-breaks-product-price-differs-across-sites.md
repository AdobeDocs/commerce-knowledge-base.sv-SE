---
title: 'MDVA-33453: Förhandsvisningen i Page Builder bryter produktpriset olika för olika webbplatser'
description: MDVA-33453-korrigeringen löser problemet där Page Builder-förhandsvisningen fungerar om matchande produkter har olika pris för olika webbplatser. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 är installerat. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.
exl-id: 78a7f7d4-8691-4b5d-a900-1c9a6ec73486
feature: CMS, Orders, Page Builder, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-33453: Förhandsvisningen i Page Builder bryter produktpriset olika för olika webbplatser

MDVA-33453-korrigeringen löser problemet där Page Builder-förhandsvisningen fungerar om matchande produkter har olika pris för olika webbplatser. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 är installerat. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:** Adobe Commerce i molninfrastruktur 2.4.1

**Kompatibel med Adobe Commerce:** Adobe Commerce om molninfrastruktur och Adobe Commerce lokalt 2.3.6 - 2.4.1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Förhandsgranskningen av Page Builder avbryts när det finns en produkt med olika priser på olika webbplatser.

<u>Steg som ska återskapas</u>:

1. Logga in på Commerce Admin-panelen.
1. Skapa två webbplatser.
1. Skapa en enkel produkt.
1. Ange olika pris för produkten på respektive webbplats.
1. Kör cron och indexera om.
1. Skapa eller redigera en CMS-sida och använd produktblocket för att lägga till produkten.

<u>Faktiskt resultat</u>:<br>

Följande fel inträffar:

*Det gick inte att filtrera mallen: Det finns redan ett objekt (Magento\\Catalog\\Model\\Product\\Interceptor) med samma ID &quot;2&quot;.*

<u>Förväntat resultat</u>:<br>

Inga fel visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
