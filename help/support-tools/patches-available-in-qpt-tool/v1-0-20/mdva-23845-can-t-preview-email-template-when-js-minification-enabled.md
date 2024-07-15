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

Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 är installerat. Korrigerings-ID är MDVA-23845. Observera att problemet korrigerades i Magento version 2.3.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Magento-version:** Magento Commerce Cloud 2.3.3

**Kompatibel med Magento-versioner:** Magento Commerce och Magneto Commerce Cloud 2.3.2-2.3.4-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u> :

1. Aktivera **JS-miniatyr** i **Admin > Lager > Konfiguration > JavaScript-inställningar > Minimera JavaScript-filer** = *Ja* .
1. Byt Magento till produktionsläge.
1. Gå till **Admin > Marknadsföring > Kommunikation > E-postmallar** .
1. Klicka på **Lägg till ny mall** .
1. Välj mallen **Ny ordning**.
1. Klicka på knappen **Läs in mall**.
1. Fyll i **mallnamn** med **Ny ordning.**
1. Klicka på knappen **Spara mall**.
1. Klicka på länken **Förhandsgranska** i kolumnen **Åtgärder** i stödrastret för e-postmallar.

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

* [Verktyget Kvalitetspatchar släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [Leta efter Magento-problem med verktyget för kvalitetspatchar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Mer information om andra tillgängliga korrigeringsfiler i QPT-verktyget finns i avsnittet [Patchar i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
