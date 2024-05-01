---
title: 'MDVA-22383: indexerare för målregler tar lång tid att indexera'
description: MDVA-22383-korrigeringen löser problemet där omindexering av produkt-/målregel- och målregel-/produktindexerare tar för lång tid. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 är installerat. Korrigerings-ID är MDVA-22383. Observera att problemet har åtgärdats i Adobe Commerce 2.3.5.
exl-id: fbf28983-5883-4769-90bd-1c97c2b2e2b8
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-22383: indexerare för målregler tar lång tid att indexera

MDVA-22383-korrigeringen löser problemet där omindexering av produkt-/målregel- och målregel-/produktindexerare tar för lång tid. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 är installerat. Korrigerings-ID är MDVA-22383. Observera att problemet har åtgärdats i Adobe Commerce 2.3.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:** Adobe Commerce om molninfrastruktur 2.3.2

**Kompatibel med Adobe Commerce:** Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.0-2.3.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det tar för lång tid att indexera om produkt-/målregel- och målregel-/produktindexerare.

<u>Förutsättningar:</u> problemet inträffar när det finns ett stort antal produkter.

<u>Steg som ska återskapas:</u>

1. Skapa en målregel med produkter för att matcha villkoren. Villkoren ska lägga till fler produkter i samlingen och ha attribut (inte kategorier eller attributuppsättning).
1. Kör följande kommando:

   ```bash
       bin/magento indexer:reindex targetrule_product_rule
   ```

<u>Faktiskt resultat:</u>

Omindexering har fastnat; produktsparandet har fastnat.

<u>Förväntat resultat:</u>

Omindexering har slutförts.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) -avsnitt.
