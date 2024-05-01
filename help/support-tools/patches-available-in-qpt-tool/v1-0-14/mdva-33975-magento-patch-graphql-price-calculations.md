---
title: 'MDVA-33975 patch: GraphQL price culations'
description: Korrigeringen MDVA-33975 åtgärdar GraphQL prisberäkningsproblem. Exempel:"
exl-id: a8266334-72cb-4b50-9ff5-9a977d762e5c
feature: GraphQL, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# MDVA-33975-korrigering: GraphQL prisberäkningar

Korrigeringen MDVA-33975 åtgärdar GraphQL prisberäkningsproblem. Det kan handla om:

* När en katalogprisregel tillämpas på en viss kundgrupp, beräknas inte artikelpriserna i kundvagnen och ordersumman korrekt i GraphQL.
* Katalogprisregler ingår inte i `CartItemPrices` i API:t.
* Kundgruppspris för den allmänna kunden läggs inte till i svaret på GraphQL produktfråga.
* Om offertsummorna beräknas om innan ett svar ges om offertpriser går tillämpade regler förlorade.
* Rabatten för fraktbelopp hämtades inte vid det senaste faktureringssteget och totalsumman visades felaktigt.
* Rabatten gäller inte i GraphQL när kundsegmentet används i kundprisregelvillkoret.

Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.14 är installerat.

## Berörda produkter och versioner

* Korrigeringen är avsedd för Adobe Commerce lokalt 2.4.1.
* Korrigeringen är även kompatibel med följande Adobe Commerce-versioner: Adobe Commerce lokalt och Adobe Commerce i molninfrastrukturen 2.3.4 - 2.4.1.

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Tillämpa korrigeringen

Använd följande länkar, beroende på vilken Adobe Commerce-produkt du använder, för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som finns i QPT-verktyget finns i [Patchar tillgängliga i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
