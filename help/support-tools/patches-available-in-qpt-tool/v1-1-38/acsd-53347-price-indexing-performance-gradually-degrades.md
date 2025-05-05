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

Korrigeringsfilen ACSD-53347 åtgärdar ett problem där prestandan gradvis försämras vid omindexering av priser för en stor produktkatalog. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 har installerats. Korrigerings-ID är ACSD-53347. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du indexerar om priser för en stor produktkatalog försämras prestanda för de frågor som körs under indexeringsprocessen gradvis.

<u>Steg som ska återskapas</u>:

1. Skapa en stor enkel katalog och tilldela anpassade alternativ till dessa produkter (anpassade alternativ använder en tillfällig tabell vid indexering).
1. Skapa minst 200 kundgrupper för att öka problemets synlighet.
1. Skapa minst tio webbplatser och tilldela alla produkter till var och en av dem.
1. Observera att de importerade produkterna är nästan identiska och endast skiljer sig åt med SKU och namn.
1. Aktivera **[!UICONTROL DB Logging]**.
1. Kör kommandot `bin/magento index:reindex catalog_product_price`.
1. Kontrollera om det finns *DELETE FRÅN`catalog_product_index_price_opt_agr_temp`* i `db.log`.

<u>Förväntade resultat</u>:

Körningen av *DB-frågorna* körs effektivt.

<u>Faktiska resultat</u>:

Prestandan för *DB-frågor* i temporära tabeller blir långsam övertid, vilket innebär att prisindexeringstabellen tar lång tid att slutföra.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
