---
title: '"MDVA-43731: Söksynonymer fungerar inte när ett värde läggs till i "Minimivillkor att matcha""'
description: Korrigeringen MDVA-43731 åtgärdar ett problem där söksynonymer slutar att fungera när ett värde läggs till i"Minimala villkor att matcha". Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 är installerat. Korrigerings-ID är MDVA-43731. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: b795989c-d10b-443e-aebe-f3859930396a
feature: Cache, Marketing Tools, Search
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# MDVA-43731: Söksynonymer fungerar inte när ett värde läggs till i Minimivillkor för matchning

Korrigeringen MDVA-43731 åtgärdar ett problem där söksynonymer slutar att fungera när ett värde läggs till i&quot;Minimala villkor att matcha&quot;. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 är installerat. Korrigerings-ID är MDVA-43731. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Söksynonymer slutar att fungera när ett värde läggs till i &quot;Minimivillkor att matcha&quot;.

<u>Steg som ska återskapas</u>:

1. Installera Adobe Commerce med exempeldata.
1. Konfigurera Elasticsearch7 som sökmotor.
1. Sök efter ordet &quot;Jacket&quot;. En lista över produkter visas.
1. Lägg till parametern [4&lt;60%] i **Konfiguration** > **Katalog** > **Katalogsökning** > **Minimivillkor som ska matchas**.
1. Rensa konfigurationscachen och gör en omindexering.
1. Sök igen efter ordet &quot;Jacket&quot; och lägg märke till att en lista med produkter visas.
1. Gå till **Marknadsföring** > **SEO &amp; Search** > **Sök synonymer**.
1. Skapa söksynonymer genom att lägga till följande synonymer: jacka, vätekare, express plus.
1. Gör en omindexering.
1. Gör en produktsökning med någon av synonymerna. T.ex. jacka.

<u>Förväntade resultat</u>:

Du får samma produktlista som tidigare i sökresultaten.

<u>Faktiska resultat</u>:

Ingen produkt visas i sökresultatet.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i vår utvecklardokumentation.
