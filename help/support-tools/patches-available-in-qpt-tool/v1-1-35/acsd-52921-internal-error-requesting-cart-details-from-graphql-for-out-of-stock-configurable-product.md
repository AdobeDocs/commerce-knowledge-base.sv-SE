---
title: 'ACSD-52921: Fel vid begäran om kundvagnsinformation från GraphQL för ej lagrad konfigurerbar produkt'
description: Använd patchen ACSD-52921 för att åtgärda Adobe Commerce-problemet när ett internt fel inträffar när kundvagnsinformation begärs från GraphQL för en ej lagrad konfigurerbar produkt.
feature: GraphQL, Configuration, Products, Shopping Cart
role: Admin
exl-id: 687460c4-f0d5-45d2-82b1-dda2947fe1e7
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-52921: Fel vid begäran om kundvagnsinformation från GraphQL för produkt som inte finns i lager

Korrigeringsfilen ACSD-52921 åtgärdar ett problem där ett internt fel inträffar när kundvagnsinformation begärs från GraphQL för en ej lagrad konfigurerbar produkt. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.35 är installerat. Korrigerings-ID är ACSD-52921. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett internt fel inträffar när kundvagnsinformation begärs från GraphQL för en produkt som inte är lagrad.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt med några alternativ.
1. Lägg till ett alternativ för ovanstående konfigurerbara produkt i kundvagnen från frontend (gästutcheckning).
1. Skaffa `[ masked_id ]` från `[ quote_id_mask ]` db-tabell för den offert som skapats ovan.
1. Kör följande GraphQL-fråga för att få information om gästvagnen ovan.

   Lägg till `[ masked_id ]` har tagits emot från steg 3 i frågan.

   ```GraphQL
   {
       cart(cart_id: "masked_id") {
           items {
               product {
                   name
                   sku
               }
               ... on ConfigurableCartItem {
                   configurable_options {
                       configurable_product_option_uid
                       option_label
                       configurable_product_option_value_uid
                       value_label
                   }
               }
               quantity
               errors {
                   code
                   message
               }
           }
       }
   }   
   ```

1. Då returneras offertinformationen utan några problem.
1. Gå till serverdelen och uppdatera den konfigurerbara produktens *[!UICONTROL Stock Status]* till *[!UICONTROL Out of Stock]*.
1. Kör samma GraphQL-fråga som i steg 4.

<u>Förväntade resultat</u>:

Felmeddelandet skickas/behandlas korrekt i svaret.

<u>Faktiska resultat</u>:

*500 intern server* fel genereras som svar på GraphQL-frågan.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
