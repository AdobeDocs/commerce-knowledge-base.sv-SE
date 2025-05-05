---
title: 'ACSD-48627: Konfigurerbar produkt som inte finns i lager orsakar ett fel'
description: Använd patchen ACSD-48627 för att åtgärda Adobe Commerce-problemet där den konfigurerbara produkten som inte finns i lager orsakar ett fel när en GraphQL-begäran skickas för att få kundvagnsinformation.
exl-id: e3048a91-1112-49a7-afcc-e6bb23208351
feature: Admin Workspace, Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-48627: Konfigurerbar produkt som inte finns i lager orsakar ett fel

Korrigeringen ACSD-48627 åtgärdar ett problem där den konfigurerbara produkten som inte finns i lager orsakar ett fel när en GraphQL-begäran skickas för att få kundvagnsinformation. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 har installerats. Korrigerings-ID är ACSD-48627. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.5-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Olagrad konfigurerbar produkt orsakar ett fel när en GraphQL-begäran skickas för att få kundvagnsinformation.

<u>Steg som ska återskapas</u>:

1. Skapa ett kundkonto.
1. Lägg några produkter i kundvagnen, inklusive en konfigurerbar produkt.
1. Gå till administratörens serverdel och redigera den konfigurerbara produkten genom att ställa in alla underordnade produkter till 0.
1. Den konfigurerbara produkten blir inte i lager eftersom alla underordnade produkter inte finns i lager.
1. Kontrollera tabellen `catalog_product_index_price`. Posten med den här produkten är tom.
1. Gör en GraphQL-förfrågan om kundens token.

   ```GraphQL
   mutation {
       generateCustomerToken(
           email: "test@example.com"
           password: "xxxx"
           ) {
               token
               }
               }
   ```

1. Gör en GraphQL-förfrågan om att hämta cartId.

   ```GraphQL
   Headers: Authentication => Bearer [customer token in step 6]
   ```

   ```GraphQL
   {
       customerCart {
           id
           items {
               id
               product {
                   name
                   sku
                   }
                   quantity
                   }
                   }
                   }
   ```

1. Begär att få kundvagnsinformation från GraphQL.

   ```GraphQL
   Headers: Authentication => Bearer [customer token in step 6]
   ```

   ```GraphQL
   query GetCartDetails($cartId: String!) {
       cart(cart_id: $cartId) {
           id
           ...CartPageFragment
           __typename
           }
           }
           fragment CartPageFragment on Cart {
               id
               total_quantity
               ...AppliedCouponsFragment
               ...ProductListingFragment
               ...PriceSummaryFragment
               __typename
               }
               fragment AppliedCouponsFragment on Cart {
                   id
                   applied_coupons {
                       code
                       __typename
                       }
                       __typename
                       }
                       fragment ProductListingFragment on Cart {
                           id
                           items {
                               uid
                               product {
                                   uid
                                   name
                                   sku
                                   url_key
                                   url_suffix
                                   thumbnail {
                                       url
                                       __typename
                                       }
                                       small_image {
                                           url
                                           __typename
                                           }
                                           stock_status
                                           price_range {
                                               minimum_price {
   
                                               final_price {
                                                   currency
                                                   value
                                                   __typename
                                                   }
                                                   regular_price {
                                                       currency
                                                       value
                                                       __typename
                                                       }
                                                       __typename
                                                       }
                                                       __typename
                                                       }
                                                       stock_status
                                                       ... on ConfigurableProduct {
                                                           variants {
                                                               attributes {
                                                                   uid
                                                                   __typename
                                                                   }
                                                                   product {
                                                                       uid
                                                                       small_image {
                                                                           url
                                                                           __typename
                                                                           }
                                                                           stock_status
                                                                           __typename
                                                                           }
                                                                           __typename
                                                                           }
                                                                           __typename
                                                                           }
                                                                           __typename
                                                                           }
                                                                           prices {
                                                                               price {
                                                                                   currency
                                                                                   value
                                                                                   __typename
                                                                                   }
                                                                                   __typename
                                                                                   }
                                                                                   quantity
                                                                                   ... on
                                                                                   ConfigurableCartItem {
                                                                                       configurable_options {
                                                                                           id
                                                                                           configurable_product_option_uid
                                                                                           option_label
                                                                                           configurable_product_option_value_uid
                                                                                           value_label
                                                                                           __typename
                                                                                           }
                                                                                           __typename
                                                                                           }
                                                                                           __typename
                                                                                           }
                                                                                           __typename
                                                                                           }
                                                                                           fragment PriceSummaryFragment on Cart {
                                                                                               id
                                                                                               items {
                                                                                                   uid
                                                                                                   quantity
                                                                                                   __typename
                                                                                                   }
                                                                                                   ...ShippingSummaryFragment
                                                                                                   prices {
                                                                                                       ...TaxSummaryFragment
                                                                                                       ...DiscountSummaryFragment
                                                                                                       ...GrandTotalFragment
                                                                                                       subtotal_excluding_tax {
                                                                                                           currency
                                                                                                           value
                                                                                                           __typename
                                                                                                           }
                                                                                                           subtotal_including_tax {
                                                                                                               currency
                                                                                                               value
                                                                                                               __typename
                                                                                                               }
                                                                                                               __typename
                                                                                                               }
                                                                                                               __typename
                                                                                                               }
                                                                                                               fragment DiscountSummaryFragment on
                                                                                                               CartPrices {
                                                                                                                   discounts {
                                                                                                                       amount {
                                                                                                                           currency
                                                                                                                           value
                                                                                                                           __typename
                                                                                                                           }
                                                                                                                           label
                                                                                                                           __typename
                                                                                                                           }
                                                                                                                           __typename
                                                                                                                           }
                                                                                                                           fragment GrandTotalFragment on CartPrices {
                                                                                                                               grand_total {
                                                                                                                                   currency
                                                                                                                                   value
                                                                                                                                   __typename
                                                                                                                                   }
                                                                                                                                   __typename
                                                                                                                                   }
                                                                                                                                   fragment ShippingSummaryFragment on Cart {
                                                                                                                                       id
                                                                                                                                       shipping_addresses {
                                                                                                                                           selected_shipping_method {
                                                                                                                                               amount {
                                                                                                                                                   currency
                                                                                                                                                   value
                                                                                                                                                   __typename
                                                                                                                                                   }
                                                                                                                                                   __typename
                                                                                                                                                   }
                                                                                                                                                   street
                                                                                                                                                   __typename
                                                                                                                                                   }
                                                                                                                                                   __typename
                                                                                                                                                   }
                                                                                                                                                   fragment TaxSummaryFragment on CartPrices {
                                                                                                                                                       applied_taxes {
                                                                                                                                                           amount {
                                                                                                                                                               currency
                                                                                                                                                               value
                                                                                                                                                               __typename
                                                                                                                                                               }
                                                                                                                                                               __typename
                                                                                                                                                               }
                                                                                                                                                               __typename
                                                                                                                                                               }
   ```

<u>Förväntade resultat</u>:

Inget *internt serverfel* i svaret.

<u>Faktiska resultat</u>:

Svaret innehåller ett *internt serverfel*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
