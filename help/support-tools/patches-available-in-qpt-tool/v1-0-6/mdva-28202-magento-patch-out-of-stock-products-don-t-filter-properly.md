---
title: "MDVA-28202 patch: out of stock products don't filter correctly"
description: MDVA-28202-korrigeringen åtgärdar ett problem där produkter i lager inte filtreras korrekt med hjälp av **Price**-filtret på en Adobe Commerce-butik. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6 är installerat.
exl-id: 45976602-15f3-4fef-9d90-da2b3fe6046d
feature: Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-28202-korrigering: Produkterna i lager filtreras inte korrekt

MDVA-28202-korrigeringen åtgärdar ett problem där produkter i lager inte har filtrerats korrekt med filtret **Price** på en Adobe Commerce-butik. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6 är installerat.

## Berörda produkter och versioner

* Korrigeringen har utformats för Adobe Commerce i molninfrastruktur 2.3.5-p1.
* Korrigeringen är även kompatibel med Adobe Commerce lokalt och Adobe Commerce i molninfrastrukturen 2.3.4 - 2.4.1.

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Slut på stockprodukter filtreras inte korrekt med filtret **Price** i Commerce Admin.

<u>Förutsättning:</u>

* Ange **Visa utanför Stock-produkter** = *Ja* under **Lager > Konfiguration > KATALOG > Lager > Stock-alternativ**.

<u>Steg att återskapa:</u>

1. Skapa en konfigurerbar produkt med två enkla produkter (Exempel: set **Price** = *$1500*).
1. Båda enkla produkter ska&quot;vara ur lager&quot; när den konfigurerbara produkten skapas.
1. Tilldela den här konfigurerbara produkten till en kategori.
1. Indexera om och kontrollera tabellen `catalog_product_index_price` med enhets-ID för ovanstående konfigurerbara produkt.
1. Spara alla produktpriser = *$0*.
1. Läs in kategorin och bekräfta att produkten är tillgänglig.
1. Öppna filtret **Pris** från lagernavigering.
1. Observera att filtret **Price** har alternativet *$0.00 - $9.99*.
1. Klicka på det här ovan nämnda filteralternativet **Price** och ange filteralternativet **Price** = *$1500* så får du den konfigurerbara produkt vi skapade ovan.

<u>Förväntat resultat:</u>

Produkten filtrerar enligt rätt prisintervall som förväntat.

<u>Faktiskt resultat:</u>

Produkten hamnar under fel prisintervallfilter.

## Tillämpa korrigeringen

Om du vill använda enskilda korrigeringsfiler använder du följande länkar beroende på distributionsmetod:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Använd korrigeringsfiler med verktyget för kvalitetskorrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Mer information om andra tillgängliga korrigeringsfiler i QPT-verktyget finns i avsnittet [Patchar i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).

Mer information om konfigurerbara produkter finns i den här artikeln i utvecklardokumentationen: [Skapa en konfigurerbar produktsjälvstudiekurs](https://devdocs.magento.com/guides/v2.4/rest/tutorials/configurable-product/config-product-intro.html) i utvecklardokumentationen.
