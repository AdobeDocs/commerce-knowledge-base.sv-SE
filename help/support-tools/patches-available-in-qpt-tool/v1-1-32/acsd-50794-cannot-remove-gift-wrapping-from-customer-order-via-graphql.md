---
title: 'ACSD-50794: Det går inte att ta bort presenter från kundorder via GraphQL'
description: Använd patchen ACSD-50794 för att åtgärda Adobe Commerce-problemet, där användare inte kan ta bort presentförpackningarna från kundordern via GraphQL.
exl-id: 4983910c-9ea0-451e-a2b6-81485184bbce
feature: Gift, GraphQL, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-50794: Det går inte att ta bort presenter från kundorder via GraphQL

Korrigeringen ACSD-50794 åtgärdar ett problem där användare inte kan ta bort presentförpackningar från kundordern via GraphQL. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 är installerat. Korrigerings-ID är ACSD-50794. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användare kan inte ta bort presenter från kundorder via GraphQL.

<u>Steg som ska återskapas</u>:

1. Skapa en kund från frontend.
1. Skapa en enkel produkt.
1. Aktivera *[!UICONTROL Gift Messages]* genom att **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Options]** och ange *[!UICONTROL Allow Gift Messages]* = *[!UICONTROL Yes]*.
1. Skapa *[!UICONTROL Gift Wrapping]* genom att **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Gift Wrapping]**.
1. Hämta kundtoken.
1. Skapa en tom kundvagn, customerCart.
   * Lägg produkter i kundvagnen: `addProductsToCart` mutation
   * Ange faktureringsadress: `setBillingAddressOnCart` mutation
   * Ange leveransadress: `setShippingAddressesOnCart` mutation
   * Ange leveranssätt: `setShippingMethodsOnCart` mutation (flatrate)
   * Ange betalningsmetod: `setPaymentMethodOnCart` mutation (checkmo)
1. Kolla presentomslaget *Uid* med kundvagnsfrågan:

   <pre><code class="language-GraphQL">
    {
      cart(cart_id: "{{CART_ID}}") {
        available_gift_wrappings{
            uid
        }
    }
    }
    </code></pre>

1. Ange presentfigursättning med `setGiftOptionsOnCart`.
1. Kontrollera kundvagnsfrågan: kundvagn.
1. Ta bort presentfigursättning med `setGiftOptionsOnCart` (ange värdet till null).
1. Kontrollera återigen kundvagnsfrågan: kundvagn.
1. Monteringsordning: `placeOrder` mutation.
1. Kör kundfråga: kund.

   <pre><code class="language-graphql">
    query {
      customer {
        firstname
        middlename
        lastname
        suffix
        email
        orders {
            items {
                order_date
                gift_wrapping {
                    design
                    uid
                }
            }
        }
        addresses {
          firstname
          middlename
          lastname
          street
          city
          region {
            region_code
            region
          }
          postcode
          country_code
          telephone
        }
      }
    }
    </code></pre>

<u>Förväntade resultat</u>:

När en användare har ställt in en presentbrytning och ångrar den returnerar kundfrågan null.

<u>Faktiska resultat</u>:

Kundfrågan returnerar fortfarande presentomslutningen som den används.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
