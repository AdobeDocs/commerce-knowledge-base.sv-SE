---
title: 'MDVA-37779: Det går inte att lägga till konfigurerbar produkt i kundvagnen via GraphQL'
description: Adobe Commerce-korrigeringsfilen MDVA-37779 löser problemet där det inte går att lägga till en konfigurerbar produkt i kundvagnen när webbplats-ID:t inte är samma som butik-ID:t. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 är installerat. Patch-ID:t är MDVA-37779. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4. 
exl-id: 5f344896-39c3-4e17-89b8-1b987bae2968
feature: GraphQL, Configuration, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# MDVA-37779: Det går inte att lägga till konfigurerbar produkt i kundvagnen via GraphQL

Adobe Commerce-korrigeringsfilen MDVA-37779 löser problemet där det inte går att lägga till en konfigurerbar produkt i kundvagnen när webbplats-ID:t inte är samma som butik-ID:t. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 är installerat. Patch-ID:t är MDVA-37779. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce i molninfrastruktur 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det går inte att lägga till en konfigurerbar produkt i kundvagnen när webbplats-ID:t inte är lika med butiks-ID:t.

<u>Förutsättningar</u>:

Ha en andra webbplats-, butiks- och butiksvy där webb-ID:t inte är samma som butiks-ID:t.

<u>Steg som ska återskapas</u>:

1. Skapa en tom kundvagn med GraphQl-mutation `createEmptyCart`.
1. Försök lägga till en konfigurerbar produkt i kundvagnen med mutationen `addConfigurableProductsToCart`.

<u>Förväntade resultat</u>:

Produkten har lagts till i varukorgen.

<u>Faktiska resultat</u>:

Få ett fel: *Det gick inte att lägga till produkten med SKU xxxx i kundvagnen: Det gick inte att hitta webbplatsen med ID 3 som begärdes. Verifiera webbplatsen och försök igen.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.


## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT-verktyget finns i avsnittet [Patchar i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
