---
title: "MDVA-40961: Det går inte att lägga till ytterligare artikel i kundvagnen när den minsta artikelkvantiteten redan finns i kundvagnen"
description: MDVA-40961-korrigeringen åtgärdar ett problem där en ytterligare artikel inte kan läggas till i vagnen när den minsta kvantiteten av artikeln redan finns i vagnen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 är installerat. Korrigerings-ID är MDVA-40961. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: fc90c2b6-f631-49ff-81b0-e41918dd79a7
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-40961: Det går inte att lägga till ytterligare artikel i kundvagnen när den minsta artikelkvantiteten redan finns i kundvagnen

MDVA-40961-korrigeringen åtgärdar ett problem där en ytterligare artikel inte kan läggas till i vagnen när den minsta kvantiteten av artikeln redan finns i vagnen. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 är installerat. Korrigerings-ID är MDVA-40961. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det går inte att lägga till ytterligare en artikel i vagnen när den minsta kvantiteten av artikeln redan finns i vagnen.

<u>Steg som ska återskapas</u>:

1. Ange att en enkel produkt ska ha mer än en **Minsta tillåtna kvantitet i kundvagn** (till exempel två).
1. Öppna produkten i Store och lägg till två av dem i kundvagnen.
1. Stanna kvar på produktsidan och lägg till en till produkt i kundvagnen.

<u>Förväntade resultat</u>:

Den tredje produkten kan läggas i varukorgen eftersom den redan innehåller minimibeloppet.

<u>Faktiska resultat</u>:

Du får följande felmeddelande: *Det minsta antalet du kan köpa är 2*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
