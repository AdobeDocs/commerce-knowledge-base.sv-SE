---
title: 'MDVA-39181: Relaterade produktregler visar produkter från kategorin odefinierad i regel'
description: MDVA-39181-korrigeringen löser problemet där relaterade produktregler visar produkter från en kategori som inte definierats i regeln. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 är installerat. Korrigerings-ID är MDVA-39181. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: b6364d1c-2480-483a-9a83-ac91feeb14b9
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39181: Relaterade produktregler visar produkter från en kategori som inte definierats i regeln

MDVA-39181-korrigeringen löser problemet där relaterade produktregler visar produkter från en kategori som inte definierats i regeln. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 är installerat. Korrigerings-ID är MDVA-39181. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Relaterade produktregler visar produkter från kategorier som inte definierats i regeln.

<u>Förutsättningar</u>:

Installera exempeldata.

<u>Steg som ska återskapas</u>:

1. Skapa ett attributvarumärke och lägg till det i **Attributuppsättningen**.
1. Välj **Josie**, **Augusta** och **Ingrid**-fodral som du vill lägga till i kategorin Brand Kitty från **Women** > **Tops** > **Jackets**.
1. Välj **Beaumont**, **Hyperion** och **Kenobi**-schaket som du vill lägga till i Brand Kitty från **Men** > **Tops** > **Jacket-kategorin**.
1. Skapa en relaterad produkt med:

   ```markdown
   Apply To: Related Products
   Customer Segments: All
   ```

   * Produkter som ska matchas:

   ```markdown
   If ALL of these conditions are TRUE
     Category is {}
     Brand is {}
   ```

   * Produkter som ska visas:

   ```markdown
   If ALL of these conditions are TRUE
      Product Category is the same as Matched Product Category
      Product brand is Matched Product Brand
   ```

1. Öppna SKU WJ04 från frontsidan och kontrollera relaterade produkter.
1. Uppdatera kategori-ID:t från **Kvinnor** > **Tops** > **Jackets** om det skiljer sig från detta.

<u>Förväntade resultat</u>:

Endast produkter från samma varumärke och samma underkategori visas i relaterade produkter.

<u>Faktiska resultat</u>:

Samhörande produkter visas med samma varumärke men med en slumpmässig överordnad kategori.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
