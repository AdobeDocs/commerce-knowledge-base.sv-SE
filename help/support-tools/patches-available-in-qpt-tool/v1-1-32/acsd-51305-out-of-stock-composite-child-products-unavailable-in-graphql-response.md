---
title: 'ACSD-51305: Olagrade sammansatta underordnade produkter som inte är tillgängliga i GraphQL-svar'
description: Använd patchen ACSD-51305 för att åtgärda Adobe Commerce-problemet där sammansatta underordnade produkter som inte finns i lager inte är tillgängliga i GraphQL svar.
exl-id: 0f33eb62-dfd3-4d07-b095-9ee6e9983c4d
feature: Categories, GraphQL, Orders, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-51305: Olagrade sammansatta underordnade produkter som inte är tillgängliga i GraphQL-svar

Korrigeringen ACSD-51305 åtgärdar ett problem där sammansatta underordnade produkter som inte finns i lager inte är tillgängliga i GraphQL svar. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 har installerats. Korrigerings-ID är ACSD-51305. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Olagrade sammansatta underordnade produkter är inte tillgängliga i GraphQL svar.

<u>Steg som ska återskapas</u>:

1. Logga in på Admin-webbplatsen.
1. Skapa en kategori (cat1, id=3).
1. Skapa en *enkel1*-produkt (ur lager, inte synlig separat, tilldelad till *cat1*).
1. Skapa en *enkel2*-produkt (i lager, inte synlig separat, tilldelad till *cat1*).
1. Skapa en *bundle1*-produkt med de underordnade produkterna *simple1* och *simple2* som alternativknappsprodukter *option1* och tilldela den till kategorin *cat1*.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]**.

   * Ange **[!UICONTROL Display Out of Stock Products]** som *Ja*.

1. Öppna *bundle1*-produkten i butiken och se till att både *simple1* och *simple2* visas i den.
1. Kör följande GraphQL-fråga:

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

Avsnittet **[!UICONTROL Product]** i blocket **[!UICONTROL Options]** är inte tomt.

<u>Faktiska resultat</u>:

Avsnittet **[!UICONTROL Product]** inuti **[!UICONTROL Options]**-blocket är tomt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
