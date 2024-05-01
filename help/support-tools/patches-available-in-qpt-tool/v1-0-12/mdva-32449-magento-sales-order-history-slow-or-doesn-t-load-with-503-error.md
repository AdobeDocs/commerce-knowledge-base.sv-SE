---
title: "MDVA-32449: försäljningsorderhistoriken tar lång tid eller läses inte in med 503-fel"
description: MDVA-32449-korrigeringen löser problemet på Adobe Commerce där försäljningsorderhistoriken läses in långsamt eller inte läses in och ett 503-fel visas. Detta problem uppstår när fler än 13 000 kunder tilldelas ett B2B-företag. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 är installerat. Observera att detta problem har åtgärdats i Adobe Commerce 2.4.1.
exl-id: e3fd4db2-b706-4712-ba8e-270eaca7fdb2
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-32449: försäljningsorderhistoriken tar lång tid eller läses inte in med 503-fel

MDVA-32449-korrigeringen löser problemet på Adobe Commerce där försäljningsorderhistoriken läses in långsamt eller inte läses in och ett 503-fel visas. Detta problem uppstår när fler än 13 000 kunder tilldelas ett B2B-företag. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 är installerat. Observera att detta problem har åtgärdats i Adobe Commerce 2.4.1.

## Berörda produkter och versioner

Detta problem uppstår när fler än 13 000 kunder tilldelas ett B2B-företag.

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce i molninfrastruktur 2.4.1

**Kompatibel med Adobe Commerce:**

Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.0 - 2.3.5-p2, 2.4.0, 2.4.1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Åtgärdar problemet där orderhistoriken läses in mycket långsamt eller inte läses in alls.

<u>Förutsättningar</u>:

Över 13 000 kunder som tilldelats ett B2B-företag

<u>Steg som ska återskapas</u>:

1. Logga in i butiken som företagsadministratör.
1. Gå till historiksidan för försäljningsorder.

<u>Förväntade resultat</u>:

Historiksidan för försäljningsorder läses in normalt.

<u>Faktiska resultat</u>:

Sidan läses in mycket långsamt eller så kanske sidan inte läses in och ett timeout-fel visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
