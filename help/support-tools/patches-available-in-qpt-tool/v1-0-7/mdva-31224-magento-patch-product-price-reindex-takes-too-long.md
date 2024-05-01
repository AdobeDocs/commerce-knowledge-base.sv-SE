---
title: "MDVA-31224-korrigering: Produktprisomindexeringen tar för lång tid"
description: MDVA-31224-korrigeringen löser problemet när produktprisomindexeringen tar för lång tid att slutföra eller aldrig slutförs. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.7 är installerat.
exl-id: 17f83fbf-9a43-4a65-b560-5f729b037c17
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# MDVA-31224-korrigering: Produktprisomindexeringen tar för lång tid

MDVA-31224-korrigeringen löser problemet när produktprisomindexeringen tar för lång tid att slutföra eller aldrig slutförs. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.7 är installerat.

## Berörda produkter och versioner

* Korrigeringen har utformats för Adobe Commerce i molninfrastruktur 2.3.3.
* Korrigeringen är även kompatibel med Adobe Commerce lokalt och Adobe Commerce i molninfrastrukturen 2.3.3 - 2.3.4-p2.

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det tar för lång tid att slutföra omindexeringen av produktpriset, eller så slutförs aldrig indexeringen.

<u>Steg som ska återskapas:</u>

1. Skapa 6 000 paketerade produkter med 15 alternativ.
1. Skapa en paketerad produkt med 30 alternativ.
1. Kör prisomindexering från CLI:     `bin/magento indexer:reindex catalog_product_price`

<u>Förväntade resultat:</u>

Det tar 1,5 timmar eller mer att omindexera produktpriset.

<u>Faktiska resultat:</u>

Det tar kort tid (en minut eller två) att omindexera produktpriset.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
