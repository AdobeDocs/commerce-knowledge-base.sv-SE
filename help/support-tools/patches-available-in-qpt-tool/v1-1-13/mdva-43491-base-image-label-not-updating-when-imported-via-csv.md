---
title: 'MDVA-43491: Etiketten för basbilden uppdateras inte när den importeras via CSV'
description: Korrigeringen MDVA-43491 åtgärdar ett problem där "base_image_label" inte uppdateras när den importeras via en CSV-fil för en webbplats med flera lager. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 är installerat. Korrigerings-ID är MDVA-43491. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: d744423a-f582-4410-8d66-861229cce1b5
feature: Data Import/Export
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MDVA-43491: Etiketten för basbilden uppdateras inte när den importeras via CSV

MDVA-43491-korrigeringen åtgärdar problemet där `base_image_label` uppdateras inte när den importeras via en CSV-fil för en webbplats med flera lager. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 är installerat. Korrigerings-ID är MDVA-43491. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.5 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

The `base_image_label` uppdateras inte när den importeras med en CSV-fil för en webbplats med flera lager.

<u>Förutsättningar</u>:

En eller flera befintliga webbplatser, butiker och butiksvyer som inte är standard.

<u>Steg som ska återskapas</u>:

1. Skapa en ny produkt.

   * Överför en bild.
   * Tilldela produkten till nya webbplatser.

1. Exportera produkten som CSV.
1. Uppdatera `base_image_label` för varje butiksvy genom att duplicera standardraden i CSV-filen.
1. Importera CSV-filen. Den kommer att uppdatera etiketterna för varje butik korrekt, som kan verifieras under **Bilder och video** på produktredigeringssidan.
1. Exportera CSV-filen igen och uppdatera `base_image_label` kolumn med olika värden.
1. Importera CSV-filen igen.
1. Öppna produkten i Admin och kontrollera om etiketten har uppdaterats för varje butiksvy.

<u>Förväntade resultat</u>:

Alt-text (bildetikett) uppdateras med det butiksspecifika värdet enligt CSV-filen.

<u>Faktiska resultat</u>:

Alt-text (bildetikett) uppdateras inte med `base_image_label` i CSV-filen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
