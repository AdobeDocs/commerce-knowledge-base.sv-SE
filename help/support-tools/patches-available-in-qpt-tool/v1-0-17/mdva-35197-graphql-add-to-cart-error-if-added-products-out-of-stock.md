---
title: 'MDVA-35197: GraphQL add to cart error if added products out of stock'
description: MDVA-35197-korrigeringen åtgärdar ett problem där det uppstår ett fel när du lägger till i kundvagnen med GraphQL om tidigare tillagda produkter inte finns i lager. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 är installerat.
exl-id: 189312f7-a505-4ba4-b12d-662987e69374
feature: GraphQL, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-35197: GraphQL lägger till i kundvagnen om tillagda produkter inte finns i lager

MDVA-35197-korrigeringen åtgärdar ett problem där det uppstår ett fel när du lägger till i kundvagnen med GraphQL om tidigare tillagda produkter inte finns i lager. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 är installerat.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce om molninfrastruktur 2.3.6

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.3.5 - 2.3.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett fel uppstod när en produkt skulle läggas till i varukorgen via GraphQL om den andra produkten redan finns i varukorgen (som också lagts till via GraphQL) inte finns i lager.

<u>Steg som ska återskapas</u>:

1. Lägg valfri produkt i kundvagnen med GraphQL.
1. Logga in på Commerce Admin-panelen och ange att produkten inte finns i lager.
1. Prova att lägga en annan produkt i kundvagnen via GraphQL.

<u>Förväntade resultat</u>:

Produkter i lager kan läggas i varukorgen.

<u>Faktiska resultat</u>:

GraphQL-felmeddelande: *Vissa produkter är inte i lager*. Det går inte att lägga till en ny&quot;lagerförd&quot; produkt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
