---
title: 'MDVA-43605: Orderdata returnerar negativa värden för radsummor när Rest API används'
description: Korrigeringen MDVA-43605 åtgärdar ett problem där orderdata returnerar negativa värden för radsummor när Rest API används. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 är installerat. Korrigerings-ID är MDVA-43605. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 8a679e85-1681-42c3-b072-18797198bdc4
feature: REST, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# MDVA-43605: Orderdata returnerar negativa värden för radsummor när Rest API används

Korrigeringen MDVA-43605 åtgärdar ett problem där orderdata returnerar negativa värden för radsummor när Rest API används. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 är installerat. Korrigerings-ID är MDVA-43605. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.1 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Orderdata returnerar negativa värden för radsummor när Rest API används.

<u>Steg som ska återskapas</u>:

1. Möjliggör fri frakt.
1. Navigera till **Konfiguration** > **Katalog** > **Pris** > och ange katalogprisomfång = webbplats.
1. Navigera till **Konfiguration** > **Försäljning** > **Moms** och uppdatera:
   * Skatteklass för leverans = skattepliktiga varor
   * Beräkningsinställningar:
      * Katalogpris = inklusive moms
      * Leveranspris = inklusive pris
      * Tillämpar rabatt på priser = inklusive moms
   * Prisvisningsinställningar: Inklusive moms (alla fält)
   * Visningsinställningar för kundvagn: Inklusive moms (alla fält)
   * Beställningar, fakturor, kreditnotor:
      * Visa leveransbelopp = inklusive moms
1. Skapa en skattesats för USA (delstat = &#39;*&#39;), Rate Percent = 24.00
1. Skapa en momsregel med momssats ovan.
1. Skapa en kundvagnsprisregel med en viss kupong och Rabatt = $50 av det fasta beloppet för hela vagnen.
1. Skapa fyra produkter till följande priser: $8,90, $5,90, $6,90 och $5,95.
1. Skapa en administratörsorder som innehåller fyra av dessa produkter med kupongkoden som skapades i föregående steg. Fraktfritt.
1. Betalning bör inte krävas eftersom kupongkoden täcker kundvagnssumman.
1. Hämta den ordning som skapades via Rest API-slutpunkten:

   ```json
   GET rest/V1/orders/1
   ```

<u>Förväntade resultat</u>:

Värdena för `base_row_total` och `base_row_total_incl_tax` i svaret är noll.

<u>Faktiska resultat</u>:

The `base_row_total` och `base_row_total_incl_tax` fält i svaret har negativa värden.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
