---
title: 'MDVA-39384: Det går inte att spara anpassat kundattribut för företagsanvändare'
description: MDVA-39384-korrigeringen löser problemet där det anpassade kundattributet för en företagsanvändare inte sparas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 är installerat. Korrigerings-ID är MDVA-39384. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: b9864ca6-307b-4649-b764-4512abc503d3
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# MDVA-39384: Det går inte att spara anpassat kundattribut för företagsanvändare

MDVA-39384-korrigeringen löser problemet där det anpassade kundattributet för en företagsanvändare inte sparas. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 är installerat. Korrigerings-ID är MDVA-39384. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.1 - 2.3.6, 2.4.1 - 2.4.3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Anpassat kundattribut för en företagsanvändare sparas inte.

<u>Förutsättningar</u>:

B2B-moduler är installerade.

<u>Steg som ska återskapas</u>:

1. Gå till **Lager** > Inställningar > **Konfiguration** > **B2B-funktioner** och ange **Aktivera företag** till Ja.
1. Skapa ett kundattribut:
   * Obligatoriska värden: Ja (valfritt, aktivera det så att valideringsfelet visas).
   * Visa på Storefront: Ja.
   * Forms att använda i: Alla finns i listan.
1. Skapa ett företag och logga in som företagsadministratör.
1. Navigera till Företagsstruktur i ditt konto.
1. Klicka på **Lägg till användare** länk.
1. Fyll i formuläret med det anpassade attributet.
1. Klicka **Spara**.

<u>Förväntade resultat</u>:

De anpassade attributvärdena sparas med den nya företagsanvändaren.

<u>Faktiska resultat</u>:

De anpassade attributvärdena sparas INTE med den nya företagsanvändaren.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
