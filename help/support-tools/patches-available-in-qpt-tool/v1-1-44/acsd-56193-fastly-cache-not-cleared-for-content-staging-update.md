---
title: '"ACSD-56193: [!DNL Fastly] cache har inte rensats för uppdatering av innehållsmellanlagring'
description: Använd korrigeringsfilen ACSD-56193 för att åtgärda Adobe Commerce-problemet där [!DNL Fastly] cache rensas inte för uppdatering av innehållstaggar.
feature: Cache, GraphQL, Staging
role: Admin, Developer
exl-id: d4bbfafa-2d24-44cf-a08b-f7dd9111a65b
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-56193: [!DNL Fastly] cache har inte rensats för uppdatering av innehållsmellanlagring

Korrigeringen ACSD-56193 åtgärdar ett problem där [!DNL Fastly] cache rensas inte för uppdatering av innehållstaggar. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 är installerat. Korrigerings-ID är ACSD-56193. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

The [!DNL Fastly/Varnish] cache har inte rensats för uppdatering av innehållsmellanlagring

<u>Steg som ska återskapas</u>:

1. Installera och konfigurera [!DNL Varnish] cache.
1. Skapa ett statiskt block med en schemalagd uppdatering.
1. Skapa en kategori som bäddar in det statiska blocket.
1. Hämta innehållet i kategorin med GraphQL-frågan nedan:

   ```GraphQL
      query GetCategories($id: String!) {
         categoryList(filters: { category_uid: { eq: $id } }) 
       {
           meta_title
           meta_keywords
           meta_description
           description
           path
           cms_block {
             content
             identifier
             title
             __typename
           }
           __typename
       }
     }
     {"id":"Mwo="}
   ```

1. Kör den här frågan flera gånger och kontrollera att svaret cachelagras i [!DNL Varnish].
1. Kör kron för att tillämpa den schemalagda ändringen.
1. Kör GraphQL-frågan ovan igen.
1. Skapa ett nytt schema för samma statiska block.
1. Upprepa stegen 5-9.

<u>Förväntade resultat</u>:

Det uppdaterade innehållet returneras efter att de schemalagda uppdateringarna har körts.

<u>Faktiska resultat</u>:

Det inaktuella innehållet returneras efter att de schemalagda uppdateringarna har körts.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
