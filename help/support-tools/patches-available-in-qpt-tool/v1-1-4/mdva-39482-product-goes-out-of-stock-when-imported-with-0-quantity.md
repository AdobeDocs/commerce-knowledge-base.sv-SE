---
title: '"MDVA-39482: Produkten slutar att vara i lager om den importeras med kvantiteten "0" och backorenheter är aktiverade"'
description: MDVA-39482 åtgärdar ett problem där produkten lämnar lagret om den importeras med "0"-kvantitet när MSI och efterbeställningar är aktiverade och där tröskelvärdet för lagerutleverans är inställt på ett minus-värde. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 är installerat. Korrigerings-ID är MDVA-39482. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: 2caf461c-993d-48b3-bc47-3fa1d014deaf
feature: Data Import/Export, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-39482: Produkten slutar att vara i lager om den importeras med kvantiteten &quot;0&quot; med bakåtorder aktiverade

MDVA-39482 åtgärdar ett problem där produkten lämnar lagret om den importeras med &quot;0&quot;-kvantitet när MSI och efterbeställningar är aktiverade och där tröskelvärdet för lagerutleverans är inställt på ett minus-värde. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 är installerat. Korrigerings-ID är MDVA-39482. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce (alla distributionsmetoder) 2.4.1-p1

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produkten hamnar utanför lagret om den importeras med kvantiteten &quot;0&quot; när MSI och efterbeställningar är aktiverade och tröskelvärdet för lagerutleverans är inställt på ett minus-värde.

<u>Förutsättningar</u>:

1. MSI och exempeldata måste vara installerade.
1. Gå till **Lager** > **Konfigurationer** > **Katalog** > **Lager**:
   * Ställ in bakordrar till&quot;Tillåt kvantitet under 0&quot;
   * Ställ in ej lagrad tröskel till -10

<u>Steg som ska återskapas</u>:

1. Kontrollera att SKU:n är **I Stock** och har kvantitet **24 MB01**.
1. Importera Stock Sources CSV. Se till att du väljer Stock Sources i Entity Type:

   ```code panel
   sku,qty,out_of_stock_qty
   24-MB01,0,-10
   ```

1. Kontrollera produktens lagerstatus efter att Stock-källorna har importerats.

<u>Förväntade resultat</u>:

24 MB01 är **I Stock** i Storefront.

<u>Faktiska resultat</u>:

24 MB01 är **Ej i lager** i Storefront.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
