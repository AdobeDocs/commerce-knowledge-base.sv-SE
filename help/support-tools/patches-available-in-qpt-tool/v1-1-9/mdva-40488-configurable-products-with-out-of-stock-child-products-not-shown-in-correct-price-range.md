---
title: 'MDVA-40488: Konfigurerbara produkter med underordnade produkter utanför lagret som inte visas i rätt prisintervall'
description: MDVA-40488-korrigeringen åtgärdar ett problem där konfigurerbara produkter med underordnade produkter utanför lagret inte visas i rätt prisintervall. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 är installerat. Korrigerings-ID är MDVA-40488. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: 0c4b9f5e-ae41-409e-b244-1d7cf948ed6f
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# MDVA-40488: Konfigurerbara produkter med underordnade produkter utanför lagret visas inte i rätt prisintervall

MDVA-40488-korrigeringen åtgärdar ett problem där konfigurerbara produkter med underordnade produkter utanför lagret inte visas i rätt prisintervall. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 är installerat. Korrigerings-ID är MDVA-40488. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Konfigurerbara produkter med underordnade produkter som inte finns i lager visas inte i rätt prisintervall.

<u>Förutsättningar</u>:

Gå till Commerce Admin > **butiker** > **konfiguration** > **katalog** > **Lager** > **aktieoptioner** och ange **Visa ej lagrade produkter** konfiguration till *Ja*.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt med två associerade produkter. Till exempel: enkla produkter Red och Brown.
1. Ange lager för den enkla produkten Red och ange Stock-status till *I Stock* anger du sedan statusen Enable Product (Aktivera produkt) till *Nej*.
1. Ställ in lager för den enkla produkten Brown och ställ sedan in statusen Enable Product (Aktivera produkt) på *Ja*.
1. Kontrollera att den konfigurerbara produktStock-statusen är *I Stock*.
1. Ändra lagret för den enkla produkten Brown till 0 och ange Stock-status till *Slut på lager*.
1. För närvarande är den konfigurerbara produktStock-statusen fortfarande *I Stock*.
1. Utför omindexering.
1. Kontrollera `min_price` och `max_price` för den konfigurerbara produkten i `catalog_product_index_price` Databastabell - de två värdena har värdet 0.
1. Men om vi ställer in den konfigurerbara produktStock-statusen till *Slut på lager* och indexera om kan vi se icke-noll `min_price` och `max_price` värden för den konfigurerbara produkten.

<u>Förväntade resultat</u>:

Om alla underordnade produkter är *Slut på lager* och den konfigurerbara produkten är också *Slut på lager*, beräknas priset med hjälp av alla underordnade produkter.

<u>Faktiska resultat</u>:

The `min_price` och `max_price` värden för den konfigurerbara produkten i `catalog_product_index_price` Databastabellen anges till 0 när den konfigurerbara lagerstatusen är *I lager*, men om det är *Slut på lager* de blir värden som inte är noll.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
