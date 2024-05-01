---
title: 'MDVA-42969: Relaterad produktregel fungerar bara när kundsegmentet är inställt på alla'
description: Korrigeringen MDVA-42969 åtgärdar ett problem där den relaterade produktregeln bara fungerar när kundsegmentet är inställt på alla. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 är installerat. Korrigerings-ID är MDVA-42969. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 2877ba7a-2681-4de2-9c37-228de232424f
feature: Customer Service, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-42969: Relaterad produktregel fungerar bara när kundsegmentet är inställt på alla

Korrigeringen MDVA-42969 åtgärdar ett problem där den relaterade produktregeln bara fungerar när kundsegmentet är inställt på alla. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 är installerat. Korrigerings-ID är MDVA-42969. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Relaterad produktregel fungerar bara när kundsegmentet är inställt på alla.

<u>Steg som ska återskapas</u>:

1. Gå till **Lager** > **Konfiguration** > **Katalog** > **Regelbaserade produktrelationer** och ange **Visa relaterade produkter** = **Endast regelbaserad**.
1. Gå till **Kunder** > **Segment** och skapa ett nytt segment: **Använd på** = **Besökare och registrerade kunder**.
1. Gå till **Marknadsföring** > **Relaterade produktregler** och skapa en ny regel.

   ```code block
   Apply To = Related Products
   Customer Segments = All
   Products to Match = SKU = <select a SKU>
   Products to Display = SKU +is one of+ Constant Value (specify 1-3 products)
   ```

1. Öppna den matchande produkten i butiken och kontrollera att Produkterna som ska visas visas.
1. Ändra regeln som skapades i steg tre och ange **Kundsegment** = **Specifik** > **Segment** från steg två.
1. Öppna den matchande produkten i butiken.

<u>Förväntade resultat</u>:

Regelbaserade relaterade produkter visas i butiken för besökare i produkten eftersom kundsegmentet skapas med följande konfiguration:

**Använd på** = **Besökare och registrerade kunder**

<u>Faktiska resultat</u>:

Inga relaterade produkter visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
