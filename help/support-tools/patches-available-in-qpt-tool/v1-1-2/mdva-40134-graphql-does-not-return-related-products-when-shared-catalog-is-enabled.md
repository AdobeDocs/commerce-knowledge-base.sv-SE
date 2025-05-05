---
title: 'MDVA-40134: GraphQL returnerar inte relaterade produkter när delad katalog är aktiverad'
description: MDVA-40134-korrigeringen åtgärdar ett problem där GraphQL inte returnerar relaterade produkter när den delade katalogen är aktiverad. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 är installerat. Korrigerings-ID är MDVA-40134. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.
exl-id: 7b14355a-1c14-4c80-9426-6c40505d638b
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-40134: GraphQL returnerar inte relaterade produkter när delad katalog är aktiverad

MDVA-40134-korrigeringen åtgärdar ett problem där GraphQL inte returnerar relaterade produkter när den delade katalogen är aktiverad. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 har installerats. Korrigerings-ID är MDVA-40134. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

GraphQL returnerar inte relaterade produkter när den delade katalogen är aktiverad.

<u>Förutsättningar</u>:

B2B-moduler måste installeras.
Instansen måste vara ren med endast exempeldata.

<u>Steg som ska återskapas</u>:

1. Gå till **Lagrar** > **Konfiguration** > **Allmänt** > **B2B-funktioner** och aktivera **Företag och Delad katalog**.
1. Gå till **Katalog** > **Delad katalog** och lägg till alla produkter i den **allmänna katalogen**.
1. Använd exempeldata och ändra Joust Duffle Bag (SKU 24-MB01).
1. Under **Relaterade produkter** lägger du till de två Duffle-påsarna (ID 7 och 13).
1. Skicka en **Post**-förfrågan:

<pre>&lbrace;
  products(filter: {sku: {eq: "24-MB01"}}, sort: {name: ASC}) &lbrace;
    items &lbrace;
      related_products &lbrace;
        uid
        name
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;</pre>

<u>Förväntade resultat</u>:

Samhörande produkter visas i GraphQL svar.

<u>Faktiska resultat</u>:

Användarna får följande fel:

<pre>Returvärdet för Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor::getStoreId() måste vara av typen int, null returnerade &lbrace;"exception":"[object] (GraphQL\\Error\\Error(code: 0): Returvärdet för Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor::getStoreId() måste vara av typen int, null returnerat </pre>

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i vår utvecklardokumentation.
