---
title: 'ACSD-45781: Butik sökfält visas inte på mobilen'
description: Korrigeringen MDVA-45781 löser problemet där sökfältet på framsidan inte visas på mobilen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19 är installerat. Patch-ID:t är MDVA-45781. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.
exl-id: 0ae90f6d-1c04-4599-b21d-4d02fd6b36db
feature: Cache, Native Luma Frontend Development, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-45781: Butik sökfält för lagring visas inte på mobilen

Korrigeringen MDVA-45781 löser problemet där sökfältet på framsidan inte visas på mobilen. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19 är installerat. Patch-ID:t är MDVA-45781. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.1-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Börssökfältet visas inte på mobilen

<u>Steg som ska återskapas</u>:

1. Gå till Commerce Admin > **Lager** > **Konfiguration** > **Katalog** > **Katalogsökning** och ange:
   * Aktivera Sök i Recommendations *Nej*
   * Aktivera sökförslag för att *Nej*
1. Klicka på **Spara konfiguration** -knappen.
1. Ren cache.
1. Använd Luma-standardtemat för att bläddra med mobiler.
1. Klicka på **Sök** -knappen.

<u>Förväntade resultat</u>:

Formulär för indatasökning visas.

<u>Faktiska resultat</u>:

Ingenting händer.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
