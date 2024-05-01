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

MDVA-28202-korrigeringen åtgärdar ett problem där Stock-produkter inte filtreras korrekt med **Pris** filtret på en Adobe Commerce store front. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6 är installerat.

## Berörda produkter och versioner

* Korrigeringen har utformats för Adobe Commerce i molninfrastruktur 2.3.5-p1.
* Korrigeringen är även kompatibel med Adobe Commerce lokalt och Adobe Commerce i molninfrastrukturen 2.3.4 - 2.4.1.

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produkterna i lager filtreras inte korrekt med **Pris** i Commerce Admin.

<u>Krav:</u>

* Ange **Visa ej lagrade produkter** = &quot;*Ja*&quot; under **Stock > Configuration > CATALOG > Inventory > Stock Options**.

<u>Steg som ska återskapas:</u>

1. Skapa en konfigurerbar produkt med två enkla produkter (Exempel: set **Pris** = *1 500 dollar*).
1. Båda enkla produkter ska&quot;vara ur lager&quot; när den konfigurerbara produkten skapas.
1. Tilldela den här konfigurerbara produkten till en kategori.
1. Indexera om och kontrollera `catalog_product_index_price` register med enhets-ID för ovanstående konfigurerbara produkt.
1. Spara alla produktpriser = *$0*.
1. Läs in kategorin och bekräfta att produkten är tillgänglig.
1. Öppna **Pris** filtrera från lagerstyrd navigering.
1. Observera att **Pris** filtret har alternativet &quot; *0,00-9,99 USD* &quot;.
1. Klicka på ovanstående **Pris** filteralternativ och ange **Pris** = *1 500 dollar* och du får den konfigurerbara produkt vi skapade ovan.

<u>Förväntat resultat:</u>

Produkten filtrerar enligt rätt prisintervall som förväntat.

<u>Faktiskt resultat:</u>

Produkten hamnar under fel prisintervallfilter.

## Tillämpa korrigeringen

Om du vill använda enskilda korrigeringsfiler använder du följande länkar beroende på distributionsmetod:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Tillämpa korrigeringar med verktyget Korrigera kvalitet](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Mer information om andra korrigeringsfiler som finns i QPT-verktyget finns i [Patchar tillgängliga i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.

Mer information om konfigurerbara produkter finns i den här artikeln i utvecklardokumentationen: [Skapa en konfigurerbar produktsjälvstudiekurs](https://devdocs.magento.com/guides/v2.4/rest/tutorials/configurable-product/config-product-intro.html) i vår dokumentation för utvecklare.
