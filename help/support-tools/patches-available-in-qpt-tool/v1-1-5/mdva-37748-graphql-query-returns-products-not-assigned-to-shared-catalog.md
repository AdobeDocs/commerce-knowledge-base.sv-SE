---
title: 'MDVA-37748: GraphQL-frågan returnerar produkter som inte har tilldelats en delad katalog'
description: Korrigeringen MDVA-37748 åtgärdar ett problem där en GraphQL-fråga returnerar produkter som inte har tilldelats en delad katalog. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 är installerat. Patch-ID:t är MDVA-37748. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: 1f441882-dc14-433c-aa03-ff22483ce5a7
feature: B2B, GraphQL, Catalog Management, Categories, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# MDVA-37748: GraphQL-frågan returnerar produkter som inte har tilldelats en delad katalog

Korrigeringen MDVA-37748 åtgärdar ett problem där en GraphQL-fråga returnerar produkter som inte har tilldelats en delad katalog. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 har installerats. Patch-ID:t är MDVA-37748. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

GraphQL-frågan returnerar produkter som inte är tilldelade till en delad katalog.

<u>Förutsättningar</u>:

B2B-moduler är installerade.

<u>Steg som ska återskapas</u>:

1. Skapa två produkter och tilldela dem till en kategori:
   * Produkt 1 - Offentlig
   * Produkt 2

1. Tilldela&quot;Product 1 - Public&quot; till den delade standardkatalogen (General).
1. Skapa ytterligare en anpassad delad katalog och tilldela den till&quot;Produkt 2&quot;.
1. Skapa ett nytt företag och tilldela det till den ytterligare delade katalog som skapades i steg tre.
1. När kron exekvering/indexering har utförts på klientsidan kontrollerar du att du kan se&quot;Produkt 1 - Offentlig&quot; om du inte är inloggad.
1. Logga in som administratör för det företag som skapades i steg fyra och validera att du bara ser&quot;Produkt 2&quot;.
1. Begär en auktoriseringstoken med följande GraphQL-fråga:

   <pre>
    <code class="language-graphql">
    mutation {
      generateCustomerToken(
        email: "company.admin@exapmle.test"
        password: "password"
      ) {
        token
      }
    }
    </code>
    </pre>

1. Lägg till rubriken **Authorization Bearer value-of-token** och kör följande GraphQL-fråga:

   <pre>
    <code class="language-graphql">
    {
      products(
          filter: {},
          pageSize: 100,
          currentPage: 1
          sort: {}
        ) {
          total_count
          page_info {
            page_size
            current_page
          }
          aggregations {
            attribute_code
            count
            label
            options {
              label
              value
              count
            }
          }
          items {
            name
            sku
            created_at
            updated_at
            stock_status
            description {html}
            short_description {html}
            url_key
            url_path
            price_tiers{
              final_price{
                  value
                  currency
                }
              discount{
                  amount_off
                  percent_off
                }
              quantity
            }
            price_range {
             maximum_price {
              regular_price {
                value
              }
              final_price {
                value
              }
            }
            minimum_price {
              regular_price {
                value
              }
              final_price {
               value
              }
            }
          }
          image {
           url
          }
          thumbnail {
           url
          }
          small_image {
           url
          }
          media_gallery {
           url
          }
          ... on ConfigurableProduct {
            configurable_options {
             id

             label
             position
             use_default
             attribute_code
             values {
               value_index
               label
               swatch_data {
                 value
               }
            }
            product_id
          }
          variants {
            product {
              id
              name
              sku
              #margin
              #margin_percentage
              image {
                url
              }
              small_image {
                url
              }
              thumbnail {
                url
              }
              media_gallery{
                url
              }
              attribute_set_id
              ... on PhysicalProductInterface {
                weight
              }
              price_range {
                minimum_price {
                  regular_price {
                    value
                    currency
                  }
                }
              }
            }
            attributes {
              label
              code
              value_index
            }
          }
        }
      }

    }
}
</code>
</pre>

<u>Förväntade resultat</u>:

Antalet och produkten som returneras av GraphQL hanterar endast den produkt som tilldelats den delade katalogen som är kopplad till den inloggade användaren.

<u>Faktiska resultat</u>:

Endast &quot;Product 2&quot; returneras, men `total_count` visar två.

<pre>
<code class="language-graphql">
{
  "data": {
    "products": {
      "total_count": 2,
      "page_info": {
        "page_size": 100,
        "current_page": 1
      },
      "aggregations": [
        {
          "attribute_code": "price",
          "count": 2,
          "label": "Price",
          "options": [
            {
              "label": "0-100",
              "value": "0_100",
              "count": 1
            },
            {
              "label": "100-200",
              "value": "100_200",
              "count": 1
            }
          ]
        },
        {
          "attribute_code": "category_id",
          "count": 1,
          "label": "Category",
          "options": [
            {
              "label": "Cat 1",
              "value": "3",
              "count": 2
            }
          ]
        }
      ],
      "items": [
        {
          "name": "Product 2",
          "sku": "Product 2",
          "created_at": "2021-05-12 10:51:44",
          "updated_at": "2021-05-12 11:03:24",
          "stock_status": "IN_STOCK",
          "description": {
            "html": ""
          },
          "short_description": {
            "html": ""
          },
          "url_key": "product-2",
          "url_path": null,
          "price_tiers": [
            {
              "final_price": {
                "value": 90,
                "currency": "USD"
              },
              "discount": {
                "amount_off": 10,
                "percent_off": 10
              },
              "quantity": 1
            }
          ],
          "price_range": {
            "maximum_price": {
              "regular_price": {
                "value": 100
              },
              "final_price": {
                "value": 90
              }
            },
            "minimum_price": {
              "regular_price": {
                "value": 100
              },
              "final_price": {
                "value": 90
              }
            }
          },
          "image": {
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/image.jpg"
          },
          "thumbnail": {
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/thumbnail.jpg"
          },
          "small_image": {
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/small_image.jpg"
          },
          "media_gallery": []
        }
      ]
    }
  }
}
</code>
</pre>

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
