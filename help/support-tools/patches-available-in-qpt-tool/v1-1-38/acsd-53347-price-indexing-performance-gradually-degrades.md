---
title: 'ACSD-53347: Prisindexeringsprestanda försämrar gradvis övertid'
description: Använd patchen ACSD-53347 för att åtgärda Adobe Commerce-problemet där prestandan gradvis försämras vid omindexering av priser för en stor produktkatalog.
feature: Price Indexer
role: Admin
exl-id: 28795673-54b0-4282-bd43-344401cbe140
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-53347: Prestanda för prisindexering försämrar övertid gradvis

Korrigeringsfilen ACSD-53347 åtgärdar ett problem där prestandan gradvis försämras vid omindexering av priser för en stor produktkatalog. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 är installerat. Korrigerings-ID är ACSD-53347. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du indexerar om priser för en stor produktkatalog försämras prestanda för de frågor som körs under indexeringsprocessen gradvis.

<u>Steg som ska återskapas</u>:

1. Skapa en stor enkel katalog och tilldela anpassade alternativ till dessa produkter (anpassade alternativ använder en tillfällig tabell vid indexering).
1. Skapa minst 200 kundgrupper för att öka problemets synlighet.
1. Skapa minst tio webbplatser och tilldela alla produkter till var och en av dem.
1. Observera att de importerade produkterna är nästan identiska och endast skiljer sig åt med SKU och namn.
1. Aktivera **[!UICONTROL DB Logging]**.
1. Kör `bin/magento index:reindex catalog_product_price` -kommando.
1. Sök efter *DELETE FRÅN`catalog_product_index_price_opt_agr_temp`* i `db.log`.

<u>Förväntade resultat</u>:

Körningen av *DB-frågor* fungerar effektivt.

<u>Faktiska resultat</u>:

Prestanda för *DB-frågor* i temporära tabeller blir långsam övertid, vilket innebär att prisindexeringstabellen tar lång tid att slutföra.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
