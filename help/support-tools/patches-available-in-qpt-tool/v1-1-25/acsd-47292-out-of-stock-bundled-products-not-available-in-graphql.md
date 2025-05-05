---
title: 'ACSD-47292: Olagerförda paketprodukter är inte tillgängliga i GraphQL svar'
description: Använd patchen ACSD-47292 för att åtgärda Adobe Commerce-problemet där de färdiga paketerade produkterna inte är tillgängliga i GraphQL-svaret, även om"show out-of-stock products" är inställd på Ja.
exl-id: 377dc62f-d1cd-4292-b25d-53c498b772a9
feature: Admin Workspace, Categories, GraphQL, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# ACSD-47292: Olagerförda paketprodukter är inte tillgängliga i GraphQL svar

Korrigeringen ACSD-47292 åtgärdar ett problem där de paketerade produkter som inte finns lagrade inte är tillgängliga i GraphQL-svaret, även om [!UICONTROL Display Out-of-Stock Products] är inställd på *[!UICONTROL Yes]*. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 har installerats. Korrigerings-ID är ACSD-47292. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

De färdiga paketerade produkterna är inte tillgängliga i GraphQL-svaret även om [!UICONTROL Display Out-of-Stock Products] är inställt på *[!UICONTROL Yes]*.

<u>Steg som ska återskapas</u>:

1. Gå till Adobe Commerce Admin > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** och ställ in [!UICONTROL Display Out-of-Stock Products] på *[!UICONTROL Yes]*.
1. Skapa två enkla produkter, s1 och s2.
1. Se till att s1 inte finns i lager och inte är synlig separat och s2 finns i lager och inte är synlig separat, och tilldela dem till en kategori.
1. Skapa en paketerad produkt med minst en alternativprodukt och tilldela s1 och s2 till det här alternativet (indatatypen&quot;RadioButton&quot;).
1. Spara den paketerade produkten och tilldela den till en kategori.
1. Gå till butiken och öppna den här paketerade produkten. Alternativet s1 är inte i lager men är grått men synligt.
1. Skicka en GraphQL-förfrågan:

```GraphQL
{
  categoryList(filters: { ids: { in: ["3"] } }) {
    id
    name
    products(pageSize: 8, sort: { position: ASC }) {
      total_count
      items {
        id
        sku
        name
        ... on BundleProduct {
          url_key
          items {
            title
            sku
            options {
              quantity
              position
              is_default
              product {
                id
                name
                sku
              }
            }
          }
        }
      }
    }
  }
}
```

<u>Förväntade resultat</u>:

s1-paketalternativet listas i GraphQL-svaret eftersom [!UICONTROL Display Out-of-Stock Products] är inställt på *[!UICONTROL Yes]* och det är synligt i butiken.

<u>Faktiska resultat</u>:

s1-paketalternativet anges inte i GraphQL svar.

```GraphQL
"items": [
                                {
                                    "title": "oo1",
                                    "sku": "bundle2",
                                    "options": [
                                        {
                                            "quantity": 1,
                                            "position": 2,
                                            "is_default": false,
                                            "product": {
                                                "id": 2,
                                                "name": "s2",
                                                "sku": "s2"
                                            }
                                        }
                                    ]
                                }
                            ]
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
