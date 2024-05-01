---
title: "MDVA-40550: Produkter som saknas på klientsidan efter omindexering"
description: MDVA-40550-korrigeringen löser problemet där omindexering leder till att vissa eller alla butikskategorier saknar produkter. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 är installerat. Korrigerings-ID är MDVA-40550. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: 0aca6eb2-6eb2-4ac4-8ae1-052f671c14e5
feature: Categories, Console, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MDVA-40550: Produkter som saknas på klientsidan efter omindexering

MDVA-40550-korrigeringen löser problemet där omindexering leder till att vissa eller alla butikskategorier saknar produkter. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 är installerat. Korrigerings-ID är MDVA-40550. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Skapa en produkt.
1. Växla indexerare till **Uppdatera enligt schema**.
   * Tilldela produkten till en kategori.
1. Aktivera xdebug och gör xdebug-brytpunkter i `\Magento\Indexer\Model\Indexer::reindexAll` och `\Magento\Indexer\Model\IndexMutex::execute`.
1. Kör en **full reindex** av `catalog_category_product` med kommandot:

   ```bash
   bin/magento indexer:reindex catalog_category_product
   ```

   * Vänta tills körningen stoppas på brytpunkten `\Magento\Indexer\Model\Indexer::reindexAll`.

1. Kör en **partiell omindexering** parallellt med kommandot:

   ```bash
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Vänta tills körningen stoppas på brytpunkten `\Magento\Indexer\Model\IndexMutex::execute`. Det kommer att låsa `catalog_category_product` indexerare.
1. Återuppta körningen av hela indexeringen av `catalog_category_product` och vänta på en timeout för låsning (60 sekunder).

<u>Förväntade resultat</u>:

Inga felmeddelanden i konsolen.

<u>Faktiska resultat</u>:

Du får följande fel:

*Det gick inte att hämta lås för index: catalog_category_product.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
