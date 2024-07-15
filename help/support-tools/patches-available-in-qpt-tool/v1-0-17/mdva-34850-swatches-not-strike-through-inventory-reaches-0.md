---
title: 'MDVA-34850: Färgrutor som inte genomstrykningspris når "0"'
description: Korrigeringen MDVA-34850 åtgärdar ett problem där färgrutorna inte bryts igenom när lagret når "0" och inte syns på PDP-länken (Product Details Page) till andra färgrutor i lagret. **Visa färdiga produkter** är också inställt på *Ja* i administratörskonfigurationen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.
exl-id: 90f5cef4-137a-426d-a447-2d1aca23e6c1
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# MDVA-34850: Färgrutor som inte genomstrykningspris når &quot;0&quot;

Korrigeringen MDVA-34850 åtgärdar ett problem där färgrutorna inte bryts igenom när lagret når &quot;0&quot; och inte syns på PDP-länken (Product Details Page) till andra färgrutor i lagret. **Visa ej lagrade produkter** är också inställt på *Ja* i administratörskonfigurationen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce om molninfrastruktur 2.3.5-p2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.1 - 2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktalternativ utanför lagret visas inte på PDP-sidan när standardlagret inte används och konfigurationen **Visa produkter utanför lagret** är aktiverad.

<u>Förutsättningar</u>:

* Installera Multi-Source Inventory (MSI).
* Aktivera visning av ej lagrade produkter i [Lageralternativ](https://docs.magento.com/user-guide/configuration/catalog/inventory.html).

<u>Steg som ska återskapas</u>:

1. Skapa nytt lager \[New Stock\] och tilldela alla webbplatser till det och ovanstående källa. Nu ska standardStock inte användas.
1. Skapa en [konfigurerbar produkt](https://docs.magento.com/user-guide/catalog/product-create-configurable.html) med tre storleksalternativ: \[S,M,L\].
1. Öppna varje alternativ och lägg till kvantiteter genom att endast tilldela den anpassade källan \[ny\_källa\] som skapats. Ange också \[Source-status\] till \[In Stock\].
1. Indexera om och kontrollera den konfigurerbara produkten från frontend. Alla tre alternativen ska vara synliga.
1. Öppna en enkel produkt som tilldelats \[size:S\] från serverdelen och ange \[Source Status\] till \[Out of Stock\]. Uppdatera även kvantiteten till 0. Indexera om och kontrollera den konfigurerbara produkten från frontend.

<u>Förväntade resultat</u>:

Eftersom alternativet Visa ej lagrade produkter är aktiverat bör alla tre alternativen visas. Alternativet \[S\] som ligger utanför lagret bör inaktiveras och strykas över. Den ska visa 2 x 1 produkt med pris = 12x2 för att få information om frontend och backend.

<u>Faktiska resultat</u>:

Alternativet Ej i lager är dolt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
