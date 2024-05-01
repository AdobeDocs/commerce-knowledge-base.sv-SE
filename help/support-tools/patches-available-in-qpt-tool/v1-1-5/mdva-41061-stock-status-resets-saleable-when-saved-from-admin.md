---
title: 'MDVA-41061: Stock-status återställs till säljbar när produkten sparas från Admin'
description: MDVA-41061-korrigeringen åtgärdar ett problem där Stock-statusen återställs till säljbar när produkten sparas från administratören. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5 är installerat. Korrigerings-ID är MDVA-41061. Den senaste patchversionen finns i QPT 1.1.15 med MDVA-41061-V3 patch-ID. Observera att problemet har åtgärdats i Adobe Commerce 2.4.4.
exl-id: fd71d3e5-685f-4987-b7e7-bfd86810d865
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-41061: Stock-status återställs till säljbar när produkten sparas från Admin

MDVA-41061-korrigeringen åtgärdar ett problem där Stock-statusen återställs till säljbar när produkten sparas från administratören. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5 är installerat. Korrigerings-ID är MDVA-41061. Den senaste patchversionen finns i QPT 1.1.15 med MDVA-41061-V3 patch-ID. Observera att problemet har åtgärdats i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.2-p2, 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Lagerstatus återställs till säljbar när produkten sparas från administratören.

<u>Förutsättningar</u>:

Lagermoduler är installerade.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt med kvantitet = 1.
1. Gör en beställning med den produkt som skapats i steg 1.
1. Kör kron - kontrollera `inventory.reservations.updateSalabilityStatus` kön körs och produktlagerstatusen har ändrats till noll i `cataloginventory_stock_status` tabell.
1. Kontrollera produkten på frontend. Den ska markeras som **Slut på lager**.
1. Spara produkten i Admin utan ändringar.

<u>Förväntade resultat</u>:

* Lagerstatus ska inte uppdateras.
* Produkten ska vara **Slut på lager** på fronten.

<u>Faktiska resultat</u>:

* Enkel produkt är markerad som **I Stock** på fronten.
* Användare hämta *Begärd kvantitet är inte tillgänglig* när du försöker lägga till det i kundvagnen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
