---
title: 'MDVA-41305: Fel i GraphQL Query addProductsToWishlist for Configurable Products'
description: MDVA-41305-korrigeringen löser problemet där användare får ett fel i GraphQL-frågan "addProductsToWishlist" för konfigurerbara produkter. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 är installerat. Korrigerings-ID är MDVA-41305. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 97d4ee1c-19af-46c0-96b2-c2765899ed83
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-41305: Fel i GraphQL Query addProductsToWishlist för konfigurerbara produkter

MDVA-41305-korrigeringen löser problemet där användare får ett fel i GraphQL-frågan `addProductsToWishlist` om konfigurerbara produkter. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 är installerat. Korrigerings-ID är MDVA-41305. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När användare lägger till konfigurerbara produkter (med/utan konfiguration) i önskelistan av GraphQL, kan de inte få konfigurerbara SKU:er och konfigurerbara alternativ som svar.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt (med blå, grå och ett anpassat alternativ).
1. Öppna frontend; logga in som kund och skapa en önskelista (check önsklist_id).
1. Öppna affischmannen och skapa en kundtoken:

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      generateCustomerToken(email: "", password: "") &lbrace;
        token
      &rbrace;
     &rbrace;
     </code>
     </pre>

1. Ange denna token för auktorisering av Bearer.
1. Försök att lägga till en konfigurerbar produkt, *Blue*, i önskelistan enligt följande:

<pre>
<code class="language-graphql">
mutation &lbrace;
 addProductsToWishlist(
   wishlistId: 1
   wishlistItems: &lbrack;
     &lbrace;
       sku: "conf2"
       selected_options: &lbrack;
            "Y29uZmlndXJhYmxlLzkzLzUw"
       &rbrack;
       quantity: 1
       entered_options: &lbrack;
         &lbrace;
           uid: "Y3VzdG9tLW9wdGlvbi8x"
           value: "test"
         &rbrace;
       &rbrack;
     &rbrace;
    &rbrack;
  ) &lbrace;
    wishlist &lbrace;
      id
      items_count
      items_v2 (currentPage: 1, pageSize: 8 ) &lbrace;
        items &lbrace;
         id
         quantity
         ... on ConfigurableWishlistItem  &lbrace;
           child_sku
           customizable_options &lbrace;
             customizable_option_uid
           &rbrace;
         &rbrace;
         product &lbrace;
           uid
           name
           sku
           options_container
           ... on CustomizableProductInterface &lbrace;
             options &lbrace;
              title
              required
              sort_order
              option_id
              ... on CustomizableFieldOption &lbrace;
                value &lbrace;
                  uid
                  sku
                  price
                  price_type
                  max_characters
                &rbrace;
              &rbrace;
            &rbrace;
          &rbrace;
          price_range &lbrace;
            minimum_price &lbrace;
              regular_price &lbrace;
                currency
                value
              &rbrace;
            &rbrace;
            maximum_price &lbrace;
               regular_price &lbrace;
                 currency
                 value
               &rbrace;
             &rbrace;
           &rbrace;
         &rbrace;
       &rbrace;
     &rbrace;
   &rbrace;
  user_errors &lbrace;
    code
    message
   &rbrace;
 &rbrace;
&rbrace;
</code>
</pre>

<u>Förväntade resultat</u>:

Användarna kan se en uppsättning konfigurerade produktalternativ i det svar som anges i nyttolasten och som läggs till i önskelistan.

<u>Faktiska resultat</u>:

Användarna får ett *internt serverfel* som svar.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i vår utvecklardokumentation.
