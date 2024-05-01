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

MDVA-39181-korrigeringen löser problemet där relaterade produktregler visar produkter från en kategori som inte definierats i regeln. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 är installerat. Korrigerings-ID är MDVA-39181. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Relaterade produktregler visar produkter från kategorier som inte definierats i regeln.

<u>Förutsättningar</u>:

Installera exempeldata.

<u>Steg som ska återskapas</u>:

1. Skapa ett attributmärke och lägg till det i **Hoppar över attributuppsättning**.
1. Välj **Josie**, **Augusta** och **Inrutnät** fodral att lägga till i Brand Kitty från **Kvinnor** > **Topp** > **Kategori för fodral**.
1. Välj **Beaumont**, **Hyperion** och **Kenobi** fodral att lägga till i Brand Kitty från **Män** > **Topp** > **Kategorin jacka**.
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
1. Uppdatera kategori-ID från **Kvinnor** > **Topp** > **Jacka** om den inte är densamma som detta.

<u>Förväntade resultat</u>:

Endast produkter från samma varumärke och samma underkategori visas i relaterade produkter.

<u>Faktiska resultat</u>:

Samhörande produkter visas med samma varumärke men med en slumpmässig överordnad kategori.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
