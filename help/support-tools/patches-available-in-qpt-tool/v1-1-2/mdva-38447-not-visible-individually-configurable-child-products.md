---
title: '''MDVA-38447: Konfigurerbara underordnade produkter som inte är synliga individuellt'' returneras i GraphQL-svar och kör MySQL-frågan långsamt'''
description: MDVA-38447 Adobe Commerce-korrigeringen åtgärdar ett problem där konfigurerbara underordnade produkter som inte är synliga var för sig returneras i GraphQL-svar och gör MySQL-frågan för GraphQL-produktfrågan långsam med kategorifilter. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 är installerat. Patch-ID:t är MDVA-38447. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: 302e7458-d9ea-466a-a2ac-d86a8ee3eca3
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# MDVA-38447: Konfigurerbara underordnade produkter som inte visas individuellt returneras i GraphQL-svar och gör MySQL-frågan långsam

MDVA-38447 Adobe Commerce-korrigeringen åtgärdar ett problem där konfigurerbara underordnade produkter som inte är synliga var för sig returneras i GraphQL-svar och gör MySQL-frågan för GraphQL-produktfrågan långsam med kategorifilter. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 har installerats. Patch-ID:t är MDVA-38447. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Konfigurerbara underordnade produkter som inte visas individuellt returneras i GraphQL-svar och gör MySQL-frågan långsam för GraphQL-produktfråga med kategorifilter.

<u>Förutsättningar</u>:

B2B-moduler måste installeras.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt med enkla produkter inställda på **Inte synliga separat**.
1. Kör en **fullständig omindexering**.
1. Kör en **GraphQL-fråga** som:

<pre>fråga getFilteredProducts()
  $filter: ProductAttributeFilterInput!
  $sort: ProductAttributeSortInput!
  $search: String
  $pageSize: Int!
  $currentPage: Int!
) {
  products(
    filter: $filter
    sortera: $sort
    sökning: $search
    pageSize: $pageSize
    currentPage: $currentPage
  ) {
    total_count
    page_info {
      total_pages
      current_page
      page_size
    }
    items {
      name
      sku
    }
  }
}</pre>

Variabler:

<pre>{"filter":{"user_group":{"eq":"}},"search":"config-100","sort":{},"pageSize":200,"currentPage":1}
</pre>

<u>Förväntade resultat</u>:

Produkter med synligheten inställd på&quot;Inte synlig separat&quot; returneras inte som svar.

<u>Faktiska resultat</u>:

Produkter med synlighet inställd på&quot;Inte synlig separat&quot; returneras som svar.

## Tillämpa korrigeringen

Använd följande länkar beroende på vilken distributionstyp du har när du vill använda enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om kvalitetspatchar för Adobe Commerce finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
