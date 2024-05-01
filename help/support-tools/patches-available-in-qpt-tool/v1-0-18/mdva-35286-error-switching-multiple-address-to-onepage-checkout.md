---
title: 'MDVA-35286: Error switching Multiple Address to Onepage checkout'
description: MDVA-35286-korrigeringen åtgärdar ett problem där det uppstår ett fel om en kund har paketprodukter i vagnen och växlar från utcheckning av flera adresser till utcheckning av en sida. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 är installerat. Patch-ID:t är MDVA-35286. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: 40c98735-6054-4b25-9882-e274424b203f
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-35286: Fel vid växling av Multiple Address till Onepage-utcheckning

MDVA-35286-korrigeringen åtgärdar ett problem där det uppstår ett fel om en kund har paketprodukter i vagnen och växlar från utcheckning av flera adresser till utcheckning av en sida. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 är installerat. Patch-ID:t är MDVA-35286. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce i molninfrastruktur 2.4.1

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.4.0-2.4.1-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett fel visas om det finns en paketprodukt i kundvagnen och användaren försöker använda OnePage-utcheckning efter att ha övergett Multi-Shipping Checkout.

<u>Steg som ska återskapas</u>:

1. Logga in på kundkontot och lägg till mer än en paketprodukt i kundvagnen.
1. Klicka på länken för att visa och redigera kundvagnen.
1. Klicka på **Checka ut med flera adresser** länk.
1. Välj olika adresser för produkter som lagts till i kundvagnen.
1. Klicka **Till kundvagnen**.
1. Klicka i kundvagnen på **Gå till kassan**.

<u>Förväntade resultat</u>:

Du omdirigeras till sidan Utcheckning.

<u>Faktiska resultat</u>:

Felmeddelandet visas: *Det uppstod ett fel när din begäran bearbetades*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
