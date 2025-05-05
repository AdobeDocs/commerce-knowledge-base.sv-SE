---
title: 'MDVA-40120: GraphQL product DESC/ASC sort does not work'
description: MDVA-40120-korrigeringen löser problemet där GraphQL sortering efter DESC/ASC inte fungerar med produkter som har samma relevans eller pris. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 är installerat. Korrigerings-ID är MDVA-40120. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: f04373d6-d3e8-47ba-9261-87fad8dff327
feature: GraphQL, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# MDVA-40120: GraphQL product DESC/ASC sort does not work

MDVA-40120-korrigeringen löser problemet där GraphQL sortering efter DESC/ASC inte fungerar med produkter som har samma relevans eller pris. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 har installerats. Korrigerings-ID är MDVA-40120. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Förutsättningar</u>:

Skapa några olika produkter till samma pris.

<u>Steg som ska återskapas</u>:

1. Kör följande GraphQL-fråga:
   <pre>
    <code class="language-graphql">
    &lbrace;
      products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: ASC}) &lbrace;
        total_count
        items &lbrace;
          name
          sku
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>
1. Kontrollera svaret.
1. Ändra sorteringsordningen från **ASC** till **DESC** i GraphQL-frågan:
   <pre>
    <code class="language-graphql">
    &lbrace;
      products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: DESC}) &lbrace;
        total_count
        items &lbrace;
          name
          sku
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>
1. Kontrollera svaret.

<u>Förväntade resultat</u>:

Produktlistan i GraphQL svar bör ändras i enlighet med sorteringsordningen.

<u>Faktiska resultat</u>:

Sorteringsordningen ändras inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i vår utvecklardokumentation.
