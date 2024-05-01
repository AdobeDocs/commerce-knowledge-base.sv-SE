---
title: 'MDVA-35064: URL-omskrivningar har inte genererats för konfigureringsbara filer som skapats via API'
description: MDVA-35064-korrigeringen åtgärdar ett problem där URL-omskrivningar inte genereras för"All store views" för produkter som skapats via API. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.
exl-id: 0898c5b3-d361-4bcb-af3a-7f76ac8a23e1
feature: REST, Categories, Configuration
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# MDVA-35064: URL-omskrivningar har inte genererats för konfigureringsbara filer som skapats via API

MDVA-35064-korrigeringen åtgärdar ett problem där URL-omskrivningar inte genereras för&quot;All store views&quot; för produkter som skapats via API. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce om molninfrastruktur 2.3.5-p1

**Kompatibel med Adobe Commerce:**

Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.3-2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När konfigurerbara produkter skapas via API genereras inte URL-omskrivningar.

<u>Steg som ska återskapas</u>:

1. Skapa en ny webbplats, butik och butiksvy.
1. Skapa en ny kategori.
1. Skapa en ny produkt och tilldela den till den nya kategorin.
1. Tilldela produkten till huvudwebbplatsen och den nya webbplatsen.
1. Kontrollera URL-tabellen och se till att den innehåller poster för produkten, kategorin/produkten för varje butik på varje webbplats.
1. Ta bort produkten för den andra webbplatsen.

<u>Förväntade resultat</u>:

URL-tabellen innehåller endast poster för produkt, kategori/produkt för butikerna på den första webbplatsen.

<u>Faktiska resultat</u>:

URL-tabellen innehåller URL-skrivningar för alla butiker på alla webbplatser.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
