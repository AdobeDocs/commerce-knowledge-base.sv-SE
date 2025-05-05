---
title: 'ACSD-46213: Begäran om kategoriträd begränsad till 20 kategorier'
description: 'Korrigeringen ACSD-46213 åtgärdar ett problem där kategoriträdets begäran är begränsad till 20 kategorier. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19 är installerat. Korrigerings-ID är ACSD-46213. '
exl-id: 27a18871-8552-4ecd-9e03-0dc38d037ea0
feature: Categories
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-46213: Begäran om kategoriträd begränsad till 20 kategorier

Korrigeringen ACSD-46213 åtgärdar ett problem där kategoriträdets begäran är begränsad till 20 kategorier. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19 är installerat. Korrigerings-ID är ACSD-46213.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.


## Problem

Kategoriträdets begäran är begränsad till 20 kategorier.

<u>Steg som ska återskapas</u>:

1. Skapa en kategori under rotkategorin.
1. Skapa 24 underkategorier under rotkategorin som skapats i steg 1.
1. Kör följande GraphQL-begäran:

   <pre>
    <code class="language-graphql">
    &lbrace;
      categoryList(filters: { parent_id: { in: ["3"] } }) &lbrace;
        name
        level
        path
        url_path
        children &lbrace;
          id
          level
          name
          path
          url_path
          url_key
          children &lbrace;
            uid
            level
            name
            path
            url_path
            url_key
          &rbrace;
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>

1. Kontrollera resultaten.

<u>Förväntade resultat</u>:

Den visar 24 kategorier.

<u>Faktiska resultat</u>:

Den visar bara 20 kategorier.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i vår utvecklardokumentation.
