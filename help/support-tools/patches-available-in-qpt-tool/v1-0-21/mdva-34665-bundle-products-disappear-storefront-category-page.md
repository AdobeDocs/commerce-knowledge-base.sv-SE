---
title: 'MDVA-34665: Paketprodukter försvinner från butikskategorisidan'
description: MDVA-34665-korrigeringen åtgärdar problemet med saknade paketerade produkter på kategorisidor. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 är installerat. Korrigerings-ID är MDVA-34665. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.
exl-id: 2b393f91-de0d-4c54-89db-5e2af13f93a6
feature: Categories, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---

# MDVA-34665: paketprodukter försvinner från butikskategorisidan

MDVA-34665-korrigeringen åtgärdar problemet med saknade paketerade produkter på kategorisidor. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 är installerat. Korrigerings-ID är MDVA-34665. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce om molninfrastruktur 2.3.4-p2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.4-2.3.4-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

**Fall 1:**

<u>Förutsättningar</u>:

1. Skapa 15 000 paketerade produkter med en enkel produkt som paketalternativ. Använd inte samma enkla produkt med flera paketerade produkter.
1. Enkla produkter ska anges till *Inte synlig separat*.

<u>Steg som ska återskapas</u>:

1. Tilldela 15 kB paketerade produkter i två kategorier, 7 500 vardera.
1. Välj alla enkla produkter (15 kB) och uppdatera lagret med uppdateringarna av produktmassattribut. Vårt mål är att ha många ID:n i söktabellen (cl-tabeller är de tabeller som används av indexeraren för att ta reda på vilka poster som behöver uppdateras.)
1. Kontrollera att du har 15 000 ID i tabellen `catalogsearch_fulltext_cl`.
1. Kontrollera att indexeraren `indexer_update_all_views` körs.
1. Fråga kategorisidan kontinuerligt och observera antalet produkter.

<u>Förväntade resultat</u>:

Antalet produkter ska förbli det var efter omindexeringen.

<u>Faktiska resultat</u>:

Antalet produkter sjunker till 7 450 efter en stund. Den ligger kvar på 7 450 även efter att indexeringen är klar.

**Fall 2:**

<u>Steg som ska återskapas</u>:

1. Skapa en paketprodukt med en tillhörande enkel produkt som tillval.
1. Ändra indexeringslägena till *uppdatera enligt schema*.
1. Tilldela paketprodukten till en kategori.
1. Ändra den enkla produktens Stock-status till *slut på lager*.
1. Kör kron. Paketet försvinner från butiken.
1. Lägg tillbaka Stock i den enkla produkten och spara pengar.
1. Kör cron indexer.
1. Uppdatera kategorisidan.

<u>Förväntade resultat</u>:

Produkten finns fortfarande inte.

<u>Faktiska resultat</u>:

Paketet visas igen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
