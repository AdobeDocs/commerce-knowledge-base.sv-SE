---
title: 'MDVA-33382 patch: invalidated indexers'
description: MDVA-33382-korrigeringen löser problemet när indexerare ogiltigförklaras efter att produkter lagts till, tagits bort eller ordnats om i en kategori. Indexerare som blir ogiltiga är "catalog_category_product" , "catalogsearch_fulltext" (och deras underordnade).
exl-id: b4ac10ee-0f9d-4d7a-be72-c4d90ebadb10
feature: Catalog Management, Categories, Price Indexer
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# MDVA-33382-korrigering: ogiltiga indexerare

MDVA-33382-korrigeringen löser problemet när indexerare ogiltigförklaras efter att produkter lagts till, tagits bort eller ordnats om i en kategori. Indexerare som är ogiltiga är `catalog_category_product` , `catalogsearch_fulltext` (och deras beroenden).

Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 är installerat. Observera att problemet kommer att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:** Adobe Commerce om molninfrastruktur 2.3.4-p2

**Kompatibel med Adobe Commerce:** Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.0 - 2.4.1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Ställ in alla indexeringslägen till **Uppdatera enligt schema**.
1. Ta bort en produkt från en kategoriredigeringssida.
1. Spara kategorin.
1. Verifiera indexstatus antingen i backend eller i CLI.

<u>Förväntade resultat</u>:

Följande index är inte ogiltiga: `catalog_category_product` , `catalogsearch_fulltext` (och deras beroenden), som förväntat.

<u>Faktiska resultat</u>:

Följande index ogiltigförklaras: `catalog_category_product` , `catalogsearch_fulltext` (och deras beroenden).

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
