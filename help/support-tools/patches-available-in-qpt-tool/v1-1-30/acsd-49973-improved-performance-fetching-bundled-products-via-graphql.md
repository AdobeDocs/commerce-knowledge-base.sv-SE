---
title: 'ACSD-49973: Förbättrad prestanda vid hämtning av paketerade produkter via [!DNL GraphQL]'
description: Använd patchen ACSD-49973 för att åtgärda Adobe Commerce-problemet där prestandaförsämringar inträffar när paketerade produkter hämtas via [!DNL GraphQL].
exl-id: 7d7fce0f-40f9-4dec-aee7-1014690ccd7c
feature: GraphQL, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# ACSD-49973: Förbättrad prestandahämtning för paketerade produkter via [!DNL GraphQL]

ACSD-49973-korrigeringen förbättrar prestandahämtningen av paketerade produkter via [!DNL GraphQL]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 är installerat. Korrigerings-ID är ACSD-49973. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Prestandaförsämring inträffar när paketerade produkter hämtas via [!DNL GraphQL].

<u>Förutsättningar</u>:

Skapa 2000-paketprodukter med [Prestandaverktyg](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html).

<u>Steg som ska återskapas</u>:

1. Aktivera [!DNL DB] frågelogg:

   ```
   bin/magento dev:query-log:enable
   ```

1. Utför följande [!DNL GraphQL] fråga:

   ```GraphQL
   {
     products(
       search: "bundle"
       pageSize: 2000,
       sort: { relevance: DESC }
     ) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. Kontrollera `var/log/db.log` för begäranden till `catalog_product_bundle_selection` tabell.

<u>Förväntade resultat</u>:

Begäranden till `catalog_product_bundle_selection` tabellen ska inte finnas i `var/log/db.log`.

<u>Faktiska resultat</u>:

Det finns 2 000 förfrågningar till `catalog_product_bundle_selection` tabellen som aktiveras samtidigt, vilket leder till prestandaförsämring.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
