---
title: 'MDVA-30782: dynamiskt block visas oavsett kundvagnsregel'
description: MDVA-30782-korrigeringen åtgärdar ett problem där ett dynamiskt block visas oavsett kundvagnsregel. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: 88da8853-aae7-4fd9-82ba-a4e9fc99cf53
feature: Cache, Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-30782: dynamiskt block visas oavsett kundvagnsregel

MDVA-30782-korrigeringen åtgärdar ett problem där ett dynamiskt block visas oavsett kundvagnsregel. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce om molninfrastruktur 2.3.5-p1

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.3.5 - 2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det dynamiska blocket visas på sidan även när villkoret för den relaterade katalogprisregeln inte uppfylls.

<u>Steg som ska återskapas</u>:

1. Skapa två produkter.
1. Skapa en katalogprisregel som bara gäller för en av dessa produkter.
1. Skapa ett dynamiskt block och tilldela det nya katalogprisregeln till det.
1. Skapa en widget med följande parametrar:
   * Typ = Dynamisk blockrotering
   * Dynamiska block att visa = Angivna dynamiska block
   * Ange dynamiska block = blockera formulärsteg \#3layousuppdateringar (kan vara vilket som helst)
   * Visa på = Alla produkttyper
   * Behållare = hjälpinformation för produkten
1. Indexera om och tömma cachen.
1. Kontrollera båda produktsidorna för ett dynamiskt blockformulärssteg \#3

<u>Förväntade resultat</u>:

Dynamiskt block visas endast på den första produktsidan.

<u>Faktiska resultat</u>:

Dynamiskt block visas på båda produktsidorna. Med Dynamic Blocks to Display = Catalog Price Rule Related on step \#3 är resultatet detsamma.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
