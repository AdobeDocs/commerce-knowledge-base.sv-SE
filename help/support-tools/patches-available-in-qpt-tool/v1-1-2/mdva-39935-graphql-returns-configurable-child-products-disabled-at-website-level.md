---
title: "MDVA-39935: GraphQL returnerar konfigurerbara underordnade produkter som är inaktiverade på webbplatsnivå"
description: MDVA-39935 Adobe Commerce-korrigeringen åtgärdar ett problem där GraphQL returnerar konfigurerbara underordnade produkter som är inaktiverade på webbplatsnivå. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2 är installerat. Korrigerings-ID är MDVA-39935. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: 45bd6bd9-3572-4477-a689-d6b952a3290a
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# MDVA-39935: GraphQL returnerar konfigurerbara underordnade produkter som är inaktiverade på webbplatsnivå

MDVA-39935 Adobe Commerce-korrigeringen åtgärdar ett problem där GraphQL returnerar konfigurerbara underordnade produkter som är inaktiverade på webbplatsnivå. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2 är installerat. Korrigerings-ID är MDVA-39935. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

GraphQL returnerar konfigurerbara underordnade produkter även efter att de har inaktiverats på webbplatsnivå.

<u>Steg som ska återskapas</u>:

1. Aktivera visning av ej lagerförda produkter under **Butik** > **Konfiguration** > **Katalog** > **Lager** > **Alternativ för Stock** > **Visa ej lagrade produkter** > **Ja**.
1. Välj valfritt **Konfigurerbar produkt** som har fler än två **Enkla produkter**.
1. Inaktivera **Enkel produkt** och spara **Konfigurerbar produkt**.
1. Hämta **Konfigurerbar produkt** data med GraphQL.

<pre>
  <code class="language-graphql">
{
  products(filter: { sku: { eq: "cp1" } }) {
    items {
      __typename
      name
      sku
      ... on ConfigurableProduct {
        variants {
          product {
            __typename
            name
            sku
            color
            stock_status
          }
        }
      }
    }
  }
}
</code>
</pre>

<u>Förväntade resultat</u>:

Inaktiverade produkter visas INTE i variantresultaten.

<u>Faktiska resultat</u>:

Inaktiverade produktdata hämtas i variantresultaten.

## Tillämpa korrigeringen

Använd följande länkar beroende på vilken distributionstyp du har när du vill använda enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om kvalitetspatchar för Adobe Commerce finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
