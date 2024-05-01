---
title: "MDVA-36138: Kostnadsfri leveransregel används inte för flera varukorg"
description: Korrigeringen MDVA-36138 åtgärdar ett problem där den matchande SKU:n i gratisleveransen inte kan levereras utan kostnad när det finns flera artiklar i vagnen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 är installerat. Korrigerings-ID är MDVA-36138. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.
exl-id: 74e25ca8-e4fa-47f4-ab95-561f70e05727
feature: Orders, Shipping/Delivery, Personalization, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-36138: Gratis frakt gäller inte för flera varukorg

Korrigeringen MDVA-36138 åtgärdar ett problem där den matchande SKU:n i gratisleveransen inte kan levereras utan kostnad när det finns flera artiklar i vagnen. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 är installerat. Korrigerings-ID är MDVA-36138. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce i molninfrastruktur 2.3.4

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.3.2 och senare

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om en regel för fri frakt endast tillämpas på vissa artiklar gäller inte rabatten när det finns andra artiklar i kundvagnen.

<u>Steg som ska återskapas</u>:

1. Skapa enkla produkter - enkel1 och enkel2.
1. Konfigurera USPS (eller någon annan onlineleveransmetod):

   * Tillåtna metoder: Prioriterad e-post (en metod har valts för att inte ha en lång lista med metoder i kundvagn och utcheckning).
   * Ledig metod: Prioriterad e-post.

1. Skapa en kundvagnsregel:

   * Ange kupongkod
   * fliken Villkor: lämna tomt
   * Fliken Åtgärder:

   `Condition: SKU is simple1`
   `Free Shipping: For matching items only`

1. Lägg enkel1 i kundvagnen.
1. Använd kupongkoden.
1. Lägg enkel2 i kundvagnen.

<u>Förväntade resultat</u>:

* simple1 - borde ha fri frakt.
* simple2 - frakten ska betalas.

<u>Faktiska resultat</u>:

Fraktpriset inkluderar enkelt1 och enkelt2.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
