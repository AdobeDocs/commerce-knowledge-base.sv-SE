---
title: 'ACSD-52801: GraphQL produktfilterfråga visar inte delmatchningsresultat'
description: Använd korrigeringsfilen ACSD-52801 för att åtgärda Adobe Commerce-problemet där GraphQL produktfilterfråga inte visar partiella matchningsresultat.
feature: Products
role: Admin, Developer
exl-id: a03a4d09-ebec-4ad0-a875-48e000a29b44
source-git-commit: 40968db03939058884bca4e4aeed2ffef0462e0b
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# ACSD-52801: GraphQL produktfilterfråga visar inte delvisa matchningsresultat

Korrigeringen ACSD-52801 åtgärdar ett problem där GraphQL produktfilterfråga inte visar partiella matchningsresultat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 är installerat. Korrigerings-ID är ACSD-52801. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p2, 2.4.5-p4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

GraphQL produktfilterfråga visar inte delvisa matchningsresultat.

<u>Steg som ska återskapas</u>:

1. Installera en ren instans med exempeldata.
1. Kör följande GraphQL-fråga.

```GraphQL
{
  products(
    filter: { name: { match: "Life" } }
    sort: { position: ASC }
    pageSize: 100
    currentPage: 1
  ) {
    total_count
    items {
      url_key
      sku
      name
      meta_title
    }
  }
}
```

<u>Förväntade resultat</u>:

Det ger liknande matchningsresultat som avancerad sökning i bakgrunden genom att lägga till `match_type` ([!UICONTROL PARTIAL], [!UICONTROL FULL]) för att kontrollera resultatet. [!UICONTROL FULL] matchar fullständiga ord, och [!UICONTROL PARTIAL] matchar delar av ord som livet i livet.

<u>Faktiska resultat</u>:

Produktfilterfrågan returnerar inte resultat av partiella matchningar för söknyckelord.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
