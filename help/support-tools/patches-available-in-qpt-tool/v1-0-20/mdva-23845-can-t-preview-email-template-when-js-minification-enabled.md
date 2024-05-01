---
title: "MDVA-23845: Det går inte att förhandsgranska e-postmallen när JS-minification är aktiverat"
description: Korrigeringen MDVA-23845 Magento åtgärdar problemet när det inte går att förhandsgranska e-postmallen i Admin när JS-minification är aktiverat.
exl-id: 08579251-a0aa-4e84-9d6a-3fa2999d9c05
feature: Communications, Marketing Tools
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# MDVA-23845: Det går inte att förhandsgranska e-postmallen när JS-minification är aktiverat

Korrigeringen MDVA-23845 Magento åtgärdar problemet när det inte går att förhandsgranska e-postmallen i Admin när JS-minification är aktiverat.

Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 är installerat. Korrigerings-ID är MDVA-23845. Observera att problemet korrigerades i Magento version 2.3.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Magento-versionen:** Magento Commerce Cloud 2.3.3

**Kompatibel med Magento-versioner:** Magento Commerce och Magneto Commerce Cloud 2.3.2-2.3.4-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u> :

1. Aktivera **JS-miniatyr** in **Admin > Stores > Configuration > JavaScript Settings > Minify JavaScript Files** = *Ja* .
1. Byt Magento till produktionsläge.
1. Gå till **Admin > Marknadsföring > Kommunikation > E-postmallar** .
1. Klicka **Lägg till ny mall** .
1. Välj **Ny beställning** mall.
1. Klicka på **Läs in mall** -knappen.
1. Fyll uppåt **Mallnamn** med **Ny beställning.**
1. Klicka på **Spara mall** -knappen.
1. I stödrastret för e-postmallar klickar du på **Förhandsgranska** i **Åtgärder** kolumn.

<u>Förväntade resultat</u> :

Förhandsgranskningen av e-postmallen visas som förväntat i det öppna popup-fönstret.

<u>Faktiska resultat</u> :

Förhandsgranskningen av e-postmallen visas inte i det öppna popup-fönstret. Popup-fönstret är tomt och JS-fel kan visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på vilken Magento-produkt du använder för att tillämpa enskilda patchar:

* Magento Commerce: DevDocs [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html) .
* Magento Commerce Cloud: DevDocs [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) .

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [Kontrollera korrigering för problem med Magento med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

Mer information om andra korrigeringsfiler som finns i QPT-verktyget finns i [Patchar tillgängliga i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
