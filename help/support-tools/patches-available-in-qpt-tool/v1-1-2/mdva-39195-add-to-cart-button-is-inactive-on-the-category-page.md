---
title: 'MDVA-39195: Lägg till i kundvagnen är inaktivt på kategorisidan'
description: MDVA-39195-korrigeringen löser problemet där knappen **Lägg till i kundvagn** är inaktiv på kategorisidan när omdirigering till kundvagnen är aktiverad. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 är installerat. Korrigerings-ID är MDVA-39195. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.
exl-id: de434908-e13a-4ab5-abb1-570bcc59c83d
feature: Categories, Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# MDVA-39195: Lägg till i kundvagnen är inaktivt på kategorisidan

MDVA-39195-korrigeringen löser problemet där **Lägg i kundvagnen** Knappen är inaktiv på kategorisidan när omdirigering till kundvagnen är aktiverat. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 är installerat. Korrigerings-ID är MDVA-39195. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

The **Lägg i kundvagnen** Knappen är inaktiv på kategorisidan när omdirigering till kundvagnen är aktiverat.

<u>Steg som ska återskapas</u>:

1. Gå till **Lager** > Inställningar > **Konfiguration** > **Försäljning** > **Utcheckning**.
1. Expandera **Kundvagn** -avsnitt.
1. Ange **Efter att en produktomdirigering lagts till i kundvagnen** till Ja.
1. Gå till kategorisidan.

<u>Förväntade resultat</u>:

**Lägg i kundvagnen** är aktivt på kategorisida.

<u>Faktiska resultat</u>:

**Lägg i kundvagnen** knappen är inaktiv på kategorisidan.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
