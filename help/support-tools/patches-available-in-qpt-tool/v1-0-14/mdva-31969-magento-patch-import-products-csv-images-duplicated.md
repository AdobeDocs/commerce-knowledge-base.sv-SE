---
title: 'MDVA-31969-korrigering: import products .csv images duplicated'
description: MDVA-31969-korrigeringen åtgärdar ett problem där bilder dupliceras när två CSV-produktfiler importeras. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14 är installerat.
exl-id: 2a3c9cce-1f71-4f27-807e-12beffc379d2
feature: Data Import/Export, Products
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# MDVA-31969-korrigering: import products .csv images duplicated

MDVA-31969-korrigeringen åtgärdar ett problem där bilder dupliceras när två CSV-produktfiler importeras. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14 är installerat.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce om molninfrastruktur 2.3.4-p2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.3 - 2.3.4-p2, 2.4.0 - 2.4.1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Nya produktbilder skapas i mappen `pub/media`, även om samma bild redan finns, när du importerar produkter.

<u>Steg som ska återskapas</u>:

1. Skapa en katalog för bilder: `mkdir var/import-images`
1. Lägg till bilder i sökvägen `<install dir>/var/import-images`.
1. Importera CSV-filen för produkten två gånger.

<u>Förväntade resultat</u>:

Resultatet blir att varje produktbild bifogas en gång.

<u>Faktiska resultat</u>:

Produkterna blir dubblerade.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som är tillgängliga i QPT finns i [korrigeringsfilerna i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
