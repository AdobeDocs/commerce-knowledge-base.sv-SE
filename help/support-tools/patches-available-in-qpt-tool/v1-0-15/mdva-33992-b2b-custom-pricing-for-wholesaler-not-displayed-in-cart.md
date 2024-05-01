---
title: "MDVA-33992: Anpassade B2B-priser för grossister visas inte i varukorgen"
description: MDVA-33992-korrigeringen åtgärdar ett problem där de anpassade priserna för en B2B-kund inte återspeglas när en produkt läggs till i en kundvagn. Den här korrigeringen är tillgänglig när QPT (Quality Patches Tool) 1.0.15 är installerat. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.
exl-id: 6018fae6-762c-46c6-9497-ecf090115b7f
feature: B2B, Catalog Management, Orders, Shopping Cart
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-33992: Anpassade B2B-priser för grossister visas inte i kundvagnen

MDVA-33992-korrigeringen åtgärdar ett problem där de anpassade priserna för en B2B-kund inte återspeglas när en produkt läggs till i en kundvagn. Den här korrigeringen är tillgänglig när QPT (Quality Patches Tool) 1.0.15 är installerat. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:** Adobe Commerce i molninfrastruktur 2.4.1 med B2B

**Kompatibel med Adobe Commerce:** Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.0-2.4.1-p1 with B2B

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Anpassade priser för B2B-kunder återspeglas inte när en produkt läggs till i en kundvagn.

<u>Steg som ska återskapas</u>:

Problemet kan reproduceras för B2B-versionen med Delad katalog aktiverat.

1. Skapa ett B2B-företag med en anpassad delad katalog tilldelad.
1. Skapa en produkt i företagets anpassade katalog med ett anpassat pris (skiktpris).
1. Som B2B-kund kontrollerar du att det anpassade produktpriset visas i katalogen.
1. Som B2B-kund lägger du till produkten i kundvagnen.

<u>Förväntat resultat</u>:

Rätt pris visas i kundvagnen och matchar priset i katalogen.

<u>Faktiskt resultat</u>:

Det anpassade priset försvinner och det normala priset från standardkatalogen visas.

## Tillämpa korrigeringen

Använd följande länkar, beroende på vilken Adobe Commerce-produkt du använder, för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som finns i QPT-verktyget finns i [Patchar tillgängliga i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
