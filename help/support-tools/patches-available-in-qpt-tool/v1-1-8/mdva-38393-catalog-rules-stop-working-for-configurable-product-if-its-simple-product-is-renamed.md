---
title: 'MDVA-38393: Katalogregler slutar att fungera för konfigurerbara produkter om den enkla produkten får ett nytt namn'
description: MDVA-38393-korrigeringen åtgärdar ett problem där katalogregler slutar fungera för en konfigurerbar produkt om dess enkla produkt namnges på nytt. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 är installerat. Korrigerings-ID är MDVA-38393. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: a20856c4-8aff-427b-a404-7afe706be06f
feature: Catalog Management, Categories, Configuration, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-38393: Katalogregler slutar fungera för konfigurerbara produkter om den enkla produkten får ett nytt namn

MDVA-38393-korrigeringen åtgärdar ett problem där katalogregler slutar fungera för en konfigurerbar produkt om dess enkla produkt namnges på nytt. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 är installerat. Korrigerings-ID är MDVA-38393. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.3.5-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Katalogregler slutar fungera för en konfigurerbar produkt om den enkla produkten får ett nytt namn.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt med en associerad enkel produkt.
1. Skapa en kategori.
1. Tilldela bara den konfigurerbara produkten till den nya kategorin.
1. Skapa nya katalogregler:
   * Villkor = Kategorin innehåller \&lt;new category=&quot;&quot; id=&quot;&quot;>
   * Åtgärd = 50 % rabatt
   * Aktiv = Ja
1. Utför omindexering.
1. Kontrollera den konfigurerbara produkten i klientprogrammet (rabatten ska gälla).
1. Kontrollera `catalogrule_product` tabell (den enkla produkten ska ha en rabatt).
1. Gå till Admin och ändra namnet på den enkla produkten. Detta skulle lägga till en post i `catalogrule_product_cl` tabell.
1. Kör kronen eller `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1` -kommando.
1. Kontrollera `catalogrule_product` tabell.

<u>Förväntade resultat</u>:

Den konfigurerbara produkten har rabatt.

<u>Faktiska resultat</u>:

* Rabattposterna som skapas för de enkla produkterna saknas i `catalogrule_product` tabell.
* Den konfigurerbara produkten i klientorganisationen har det fullständiga ursprungliga priset.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
