---
title: 'MDVA-40134: GraphQL returnerar inte relaterade produkter när delad katalog är aktiverad'
description: MDVA-40134-korrigeringen åtgärdar ett problem där GraphQL inte returnerar relaterade produkter när den delade katalogen är aktiverad. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 är installerat. Korrigerings-ID är MDVA-40134. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.
exl-id: 7b14355a-1c14-4c80-9426-6c40505d638b
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-40134: GraphQL returnerar inte relaterade produkter när delad katalog är aktiverad

MDVA-40134-korrigeringen åtgärdar ett problem där GraphQL inte returnerar relaterade produkter när den delade katalogen är aktiverad. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 är installerat. Korrigerings-ID är MDVA-40134. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

GraphQL returnerar inte relaterade produkter när den delade katalogen är aktiverad.

<u>Förutsättningar</u>:

B2B-moduler måste installeras.
Instansen måste vara ren med endast exempeldata.

<u>Steg som ska återskapas</u>:

1. Gå till **Lager** > **Konfiguration** > **Allmänt** > **B2B-funktioner** och aktivera **Företag och delad katalog**.
1. Gå till **Katalog** > **Delad katalog** och lägg till alla produkter i **Allmän katalog**.
1. Använd exempeldata och ändra Joust Duffle Bag (SKU 24-MB01).
1. Under **Samhörande produkter** lägger du till de två Duffle-påsarna (ID 7 och 13).
1. Skicka en **Bokför** begäran:

<pre>{ products(filter: {sku: {eq: "24-MB01"}}, sort: {name: ASC}) { items { related_products { uid name } }}</pre>

<u>Förväntade resultat</u>:

Samhörande produkter visas i GraphQL svar.

<u>Faktiska resultat</u>:

Användarna får följande fel:

<pre>Returvärdet för Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor::getStoreId() måste vara av typen int, null returnerade {"exception":"[object] (GraphQL\\Error\\Error(code: 0): Returvärdet för Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor::getStoreId() måste vara av typen int, null returnerat </pre>

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
