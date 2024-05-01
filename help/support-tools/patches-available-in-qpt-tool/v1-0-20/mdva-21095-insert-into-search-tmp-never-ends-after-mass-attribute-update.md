---
title: 'MDVA-21095: INSERT INTO "search_tmp..." upphör aldrig efter uppdatering av massattribut'
description: Korrigeringen MDVA-21095 åtgärdar problemet när frågan "INSERT INTO" "search\_tmp..." aldrig avslutas efter en uppdatering av ett massattribut. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 är installerat. Korrigerings-ID är MDVA-21095. Observera att det inte finns någon plan för att åtgärda problemet i framtida versioner.
exl-id: fd599473-b49a-4f9c-a13f-612d05e43f09
feature: Attributes, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# MDVA-21095: INSERT INTO &quot;search_tmp...&quot; upphör aldrig efter uppdatering av massattribut

Korrigeringen MDVA-21095 åtgärdar problemet när en fråga `INSERT INTO` &quot;search\_tmp..&quot; upphör aldrig efter en uppdatering av ett massattribut. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 är installerat. Korrigerings-ID är MDVA-21095. Observera att det inte finns någon plan för att åtgärda problemet i framtida versioner.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce om molninfrastruktur 2.3.2

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.3.4-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

`INSERT INTO` &quot;search\_tmp..&quot; upphör aldrig efter en uppdatering av ett massattribut.

<u>Steg för att återskapa</u>:

Utför en uppdatering av massattributvärden med ~30 000 objekt.

<u>Förväntade resultat</u>:

Omindexeringsprocessen slutförs normalt som förväntat.

<u>Faktiska resultat</u>:

Omindexeringsprocessen slutförs, men det finns många frågor `INSERT INTO` &quot;search\_tmp..&quot; börjar tills servern når `pm.max_children` parametervärdet och PHP-fpm dör, och dessa inträffar hela tiden efter att MySQL startats om och processen avslutats.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
