---
title: 'MDVA-43862: Kunden kan inte uppdatera kundvagnsobjekt på grund av ett GraphQL UpdateCartItems-mutationsfel'
description: MDVA-43862-korrigeringen åtgärdar ett problem där kunden inte kan uppdatera kundvagnsobjekt på grund av ett GraphQL UpdateCartItems-mutationsfel. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 är installerat. Korrigerings-ID är MDVA-43862. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 5f0a2970-34a8-4a25-baf8-15c007f97084
feature: GraphQL, Orders, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-43862: Kunden kan inte uppdatera kundvagnsobjekt på grund av ett GraphQL UpdateCartItems-mutationsfel

MDVA-43862-korrigeringen åtgärdar ett problem där kunden inte kan uppdatera kundvagnsobjekt på grund av ett GraphQL UpdateCartItems-mutationsfel. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 är installerat. Korrigerings-ID är MDVA-43862. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1, 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.3 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kunden kan inte uppdatera varukorgsobjekt på grund av ett GraphQL UpdateCartItems-mutationsfel.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt (MH01) genom att tilldela en enkel (MH01-XL-Gray).
1. Gå till Commerce Admin > **Katalog** > **Produkter** > **SKU** > **MH01** > **Anpassningsbara alternativ**.
1. Lägg till ett anpassat alternativ till produkten.
   * Alternativtitel: Alternativ1
   * Alternativtyp: Fält
   * Obligatoriskt: Ja
   * Pris: 10.00
   * Pristyp: fast
   * SKU: MHC1
   * Max Characters: 25
1. Kör GraphQL-frågan nedan för att generera kundvagn-ID.

   ```GraphQL
   mutation {
     createEmptyCart
   }
   ```

1. Notera kundvagnens ID-kod.
1. Kör frågan nedan om du vill lägga till en konfigurerbar produkt i kundvagnen:

   ```GraphQL
   mutation {
   addConfigurableProductsToCart(
   input: {
       cart_id: "<cart ID from above step>",
       cart_items: [{
       parent_sku: "MH01",
       data: {
           quantity: 1,
           sku: "MH01-XL-Gray"
           },
           customizable_options: {
               id: 1,
               value_string: "2"
               }
           }
       ]
   }
   )
   {
   cart {
     items {
       uid
       quantity
       product {
         name
         sku
       }
       ... on ConfigurableCartItem {
         configurable_options {
           option_label
         }
       }
     }
   }
   }
   }
   ```

1. Du kommer att märka att vagnen är ifylld med den konfigurerbara artikeln.
1. Anteckna det uid som returnerats.
1. Kör även frågan nedan för att uppdatera kundvagnsartikeln.

   ```GraphQL
   mutation {
     updateCartItems(
       input: {
         cart_id: "<cart ID from previous step>",
         cart_items: [
           {
             cart_item_uid: "<uid from previous step>"
             quantity: 3,
             customizable_options:[{
                 id: 1,
                 value_string: "67"
             }]
           }
         ]
       }
     ){
       cart {
         items {
           uid
           product {
             name
           }
           quantity
         }
         prices {
           grand_total{
             value
             currency
           }
         }
       }
     }
   }
   ```

1. Observera svaret.

<u>Förväntade resultat</u>:

Kundvagnen uppdateras utan problem.

<u>Faktiska resultat</u>:

Du får följande fel:

```GraphQL
{
  "errors": [
    {
      "message": "Could not update cart item: You need to choose options for your item.",
      "extensions": {
        "category": "graphql-input"
      },
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "updateCartItems"
      ]
    }
  ],
  "data": {
    "updateCartItems": null
  }
}
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i vår utvecklardokumentation.
