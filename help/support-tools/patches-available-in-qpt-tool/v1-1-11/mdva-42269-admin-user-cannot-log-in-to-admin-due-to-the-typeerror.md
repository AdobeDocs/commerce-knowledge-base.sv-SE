---
title: '''MDVA-42269: Administratörsanvändaren kan inte logga in i Admin på grund av felet "TypeError"'
description: MDVA-42269-korrigeringen åtgärdar ett problem där administratörsanvändare inte kan logga in i administratören på grund av TypeError. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 är installerat.  Korrigerings-ID är MDVA-42269.  Den senaste korrigeringsuppdateringen finns i QPT 1.1.15. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 66d744a2-054e-493c-a060-9ed78447e35b
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-42269: Administratörsanvändaren kan inte logga in i Admin på grund av felet TypeError

MDVA-42269-korrigeringen åtgärdar ett problem där administratörsanvändare inte kan logga in i administratören på grund av TypeError. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 är installerat.  Korrigerings-ID är MDVA-42269.  Den senaste korrigeringsuppdateringen finns i QPT 1.1.15. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1, 2.3.7-p3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1 - 2.4.3-p2, 2.3.7-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörsanvändare kan inte logga in i administratören på grund av följande fel: *TypeError: strtotime() förväntar att parameter 1 ska vara sträng, null given.*

<u>Steg som ska återskapas</u>:

Logga in i Commerce Admin.

<u>Förväntade resultat</u>:

Administratörsanvändaren kan logga in med rätt användarnamn och lösenord.

<u>Faktiska resultat</u>:

Administratören kan inte logga in. Följande fel loggas: *TypeError: strtotime() förväntar att parameter 1 ska vara sträng, null given.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
