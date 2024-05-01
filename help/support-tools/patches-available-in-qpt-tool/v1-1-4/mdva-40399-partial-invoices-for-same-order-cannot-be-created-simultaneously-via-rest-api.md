---
title: "MDVA-40399: Det går inte att skapa partiella fakturor för samma order samtidigt via API"
description: Korrigeringen MDVA-40399 åtgärdar ett problem där partiella fakturor för samma order inte kan skapas samtidigt via Rest API. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 är installerat. Korrigerings-ID är MDVA-40399. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: 2444ba57-b30b-4fdf-9e5d-988cf7fa8dd1
feature: REST, Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# MDVA-40399: Det går inte att skapa partiella fakturor för samma order samtidigt via API

Korrigeringen MDVA-40399 åtgärdar ett problem där partiella fakturor för samma order inte kan skapas samtidigt via Rest API. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 är installerat. Korrigerings-ID är MDVA-40399. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det går inte att skapa partiella fakturor för samma order samtidigt med Rest API.

<u>Förutsättningar</u>:

En konfigurerbar produkt med minst två variationer.

<u>Steg som ska återskapas</u>:

1. Lägg båda varianterna av den konfigurerbara produkten i kundvagnen.
1. Beställ.
1. Skapa två fakturor samtidigt för ordern via Rest API.

<u>Förväntade resultat</u>:

* Båda fakturorna måste skapas.
* `qty_invoiced` ska uppdateras för båda fakturorna i `sales_order_item` tabell.
* Båda produkterna ska ha fakturerad kvantitet.

<u>Faktiska resultat</u>:

* Båda fakturorna har skapats.
* `qty_invoiced` uppdateras inte mot en av fakturorna i `sales_order_item` tabell.
* I administratörens **Ordervy** På sidan visas fakturakvantiteten endast för en produkt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
