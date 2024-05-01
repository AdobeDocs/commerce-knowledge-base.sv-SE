---
title: "ACSD-55100: [!DNL GraphQL] returnerar inte produkter som överstiger 10 kB i sökresultaten"
description: Använd patchen ACSD-55100 för att åtgärda Adobe Commerce-problemet där GraphQL inte returnerar produkter som överstiger *10 k* i sökresultaten.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 951e5cd4-9690-43df-9e51-deab73f9eb54
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# ACSD-5100: [!DNL GraphQL] returnerar inte produkter som överstiger 10 kB i sökresultaten

Korrigeringen ACSD-55100 åtgärdar ett problem där [!DNL GraphQL] returnerar inte produkter utöver *10 kB* i sökresultaten. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 är installerat. Korrigerings-ID är ACSD-55100. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!DNL GraphQL] returnerar inte produkter utöver *10 kB* i sökresultaten.

<u>Förutsättningar</u>:

Om **[!DNL OpenSearch]** kontrollerar du att du använder den senaste tillgängliga versionen.

För att lösa det rapporterade problemet introduceras funktionen för tidpunkt, som är tillgänglig efter **[!DNL OpenSearch]** 2.5.0 och kräver version 2.2 av `opensearch-project/opensearch-php` paket.

Det finns dock en konflikt med `magento/magento-cloud-metapackage`, som anger ett beroende av `opensearch-project/opensearch-php` paket som ska vara mindre än version 2.0.1.


Detta beroende förhindrar uppdatering av [opensearch-project/opensearch-php] till den senaste versionen, 2.2.

Därför påträffar systemet följande fel och returnerar null-resultat för produkter som överskrider *10 000*.

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

Det befintliga beroendet gör det svårt att lägga till en version direkt i `composer.json` och uppdatera `opensearch-project/opensearch-php` till version 2.2.

Åtgärda problemet genom att lägga in följande rad i huvudboken `composer.json` under kravblocket. Distribuera sedan om för att uppdatera det problematiska paketet till den senaste versionen.

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u>Steg som ska återskapas</u>:

1. Generera katalogen med *15 kB* produkter.
1. Skicka [!DNL GraphQL]:

```
    query {
    products(
    filter: {
    # category_id:{eq:""}
    }
    , pageSize: 5, currentPage: 1

    ) {
    total_count
    page_info {
    current_page
    page_size
    total_pages
     }

     aggregations {

    attribute_code
    count
    label
    options {
    label
    value

    }
    }

    items {
    uid
    sku
    is_for_clearance
    categories {
    name
    breadcrumbs {
    category_name
    category_uid
    }
    display_mode
    description
    }
    }
    }
    }
```

<u>Förväntade resultat</u>:

Total_count = *15 kB*
Du bör kunna visa alla produkter.

<u>Faktiska resultat</u>:

Total_count = *10 kB*
Du kan inte få fler produkter att visa efter *10 kB* grupp.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
