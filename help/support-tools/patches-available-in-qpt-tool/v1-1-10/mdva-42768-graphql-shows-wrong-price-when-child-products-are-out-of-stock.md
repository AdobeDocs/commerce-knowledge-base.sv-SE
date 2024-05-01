---
title: 'MDVA-42768: GraphQL visar fel pris när underordnade produkter inte finns i lager'
description: MDVA-42768-korrigeringen åtgärdar ett problem där GraphQL visar fel pris när de underordnade produkterna i en konfigurerbar produkt inte finns i lager. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 är installerat. Patch-ID:t är MDVA-42768. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 012e7e21-e508-4449-98a6-4bdb41284c3a
feature: GraphQL, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# MDVA-42768: GraphQL visar fel pris när underordnade produkter inte finns i lager

MDVA-42768-korrigeringen åtgärdar ett problem där GraphQL visar fel pris när de underordnade produkterna i en konfigurerbar produkt inte finns i lager. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 är installerat. Patch-ID:t är MDVA-42768. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När de underordnade produkterna för en konfigurerbar produkt inte finns i lager och inställningen Visa ej i Stock-produkter är aktiverad, visar GraphQL-frågan produktens ordinarie pris som **0**.

<u>Förutsättningar</u>:

Exempeldata har installerats.

<u>Steg som ska återskapas</u>:

1. Aktivera produktinställningen Visa utanför Stock i Commerce Admin genom att gå till **Lager** > **Konfiguration** > **Katalog** > **Lager**.
1. Skapa en konfigurerbar produkt och tilldela den en enkel underordnad produkt.
1. Ställ in lagret för variantprodukten (enkel) till **Slut på lager**.
1. Indexera om.
1. Kör följande GraphQL-fråga:

   ```GraphQL
   query {
     products(filter: { sku: { eq: "MH01" } }) {
       items {
         sku
         price_range {
           minimum_price {
             regular_price {
               value
               currency
             }
             final_price {
               value
               currency
             }
             discount {
               amount_off
               percent_off
             }
           }
           maximum_price {
             regular_price {
               value
               currency
             }
             final_price {
               value
               currency
             }
             discount {
               amount_off
               percent_off
             }
           }
         }
       }
     }
   }
   ```

1. Kontrollera svarsavsnittet `minimum_price` > `regular price`.

<u>Förväntade resultat</u>:

Det lägsta ordinarie priset visas inte som 0 som svar.

<u>Faktiska resultat</u>:

Det lägsta ordinarie priset = 0 som svar.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
