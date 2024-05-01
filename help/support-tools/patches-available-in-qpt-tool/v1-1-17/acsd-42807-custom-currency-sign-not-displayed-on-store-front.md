---
title: 'ACSD-42807: Egen valutasymbol visas inte i butiken'
description: Korrigeringen ACSD-42807 åtgärdar ett problem där den anpassade valutasymbolen inte visas i butiken. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 är installerat. Korrigerings-ID är ACSD-42807. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
exl-id: 21bd17b4-d9d8-4c40-8f89-d6f7b930b475
feature: Storefront
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-42807: Egen valutasymbol visas inte i butiken

Korrigeringen ACSD-42807 åtgärdar ett problem där den anpassade valutasymbolen inte visas i butiken. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 är installerat. Korrigerings-ID är ACSD-42807. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det anpassade valutatecknet visas inte i butiken.

<u>Steg som ska återskapas</u>:

1. Gå till **Butik** > **Inställningar** > **Konfigurationer** > **Allmänt** > **Valutainställningar** och välj en anpassad valuta. t.ex., **Mexikanska peso**.
1. Gå till **Butik** > **Inställningar** > **Konfigurationer** > **Allmänt** > **Nationella inställningar** och markera **Spanska (Mexiko)**.
1. Gå till **Butik** > **Valutasymboler** och konfigurera valutasymbolen till **MX$**.
1. Markera valutasymbolen på frontend.

<u>Förväntade resultat</u>:

Standardvalutasymbolen är &quot;MX$&quot; med valutan &quot;Mexikansk peso&quot; och den nationella inställningen &quot;Spanska (Mexiko)&quot;.

<u>Faktiska resultat</u>:

Standardvalutasymbolen visar &quot;$&quot;.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
