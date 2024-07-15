---
title: 'MDVA-36170: GraphQL-fråga till kategori returnerar inte cachelagrade data'
description: Korrigeringen MDVA-36170 åtgärdar ett problem där resultatet av GraphQL-frågan inte cachelagras. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 är installerat. Korrigerings-ID är MDVA-36170. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: 6249b751-4b71-4833-ab86-ded615d648a8
feature: Cache, GraphQL, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# MDVA-36170: GraphQL-fråga till kategori returnerar inte cachelagrade data

Korrigeringen MDVA-36170 åtgärdar ett problem där resultatet av GraphQL-frågan inte cachelagras. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 är installerat. Korrigerings-ID är MDVA-36170. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce om molninfrastruktur 2.3.6

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.3.1 - 2.4.1-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Åtgärdar problemet där resultatet av GraphQL-frågan inte cachelagras.

<u>Steg som ska återskapas</u>:

Handlaren använder metoden GET för GraphQL-cachning, men hämtar inte cachelagrade data.

<pre>https://magento_url/graphql?query={ products(filter: {category_id: {eq: "2"}}, pageSize: 2000, currentPage: 1, sort: {position: ASC}) {
items {
  sku
  id
  name
  description {
    html
  }
  url_key
  specifikationer
  image {
    label
    gallery_url
  }
  __typename
  antal_i
  small_image {
    gallery_url
    label
  }
  product_price_range {
    maximum_price {
      final_price {
        value
      }
    }
    minimum_price {
      final_price {
        value
      }
    }
  }
  ... on ConfigurableProduct {
    varianter{
      attribut{
        kod
        label
        value_index
      }
      product{
        sku
        antal_i
      }
    }
   }
  }
}
}}</pre>

<u>Förväntade resultat</u>:

Data cachelagras.

<u>Faktiska resultat</u>:

Data cachelagras inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
