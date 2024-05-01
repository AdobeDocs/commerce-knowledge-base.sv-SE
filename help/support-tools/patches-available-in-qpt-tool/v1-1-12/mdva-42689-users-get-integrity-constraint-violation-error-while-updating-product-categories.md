---
title: 'MDVA-42689: Användarna får felmeddelande om integritetsbegränsning när produktkategorier uppdateras under importen'
description: MDVA-42689-korrigeringen åtgärdar ett problem där användaren får ett integritetsbegränsningsfel när produktkategorier uppdateras under importen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 är installerat. Korrigerings-ID är MDVA-42689. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 7beff3bb-9313-43dc-be96-e33eff52a38e
feature: Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-42689: Användarna får felmeddelande om integritetsbegränsning när produktkategorier uppdateras vid import

MDVA-42689-korrigeringen åtgärdar ett problem där användaren får ett integritetsbegränsningsfel när produktkategorier uppdateras under importen. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 är installerat. Korrigerings-ID är MDVA-42689. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Adobe Commerce genererar ett integritetsbegränsningsfel när produktkategorier uppdateras under importen.

<u>Steg som ska återskapas</u>:

1. Konfigurera två webbplatser.
1. Skapa underkategorier under rotkategorin upp till två nivåer på kategorisidan. Till exempel Rotkategori > **Kugghjul** > **Bevakningar**.
1. Skapa två enkla produkter och tilldela båda produkterna till samma **Kugghjul** > **Bevakningar** kategori.
1. Tilldela en enkel produkt till båda webbplatserna.
1. Spara produkten.
1. Förbered en CSV-fil för import. Det ska finnas två produktposter med olika butiksvyer. En av produkterna bör tillhöra båda dessa butiksvyer.
1. Importera nu CSV-filen genom att navigera till **System** > **Importera** > **Enhetstyp** (Produkter).

<u>Förväntade resultat</u>:

CSV-filen importeras utan fel.

<u>Faktiska resultat</u>:

Adobe Commerce genererar följande fel:

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry '1302' for key 'PRIMARY', query was: INSERT INTO `catalog_url_rewrite_product_category` (`url_rewrite_id`,`category_id`,`product_id`) VALUES (?, ?, ?), (?, ?, ?), (?, ?, ?)
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
