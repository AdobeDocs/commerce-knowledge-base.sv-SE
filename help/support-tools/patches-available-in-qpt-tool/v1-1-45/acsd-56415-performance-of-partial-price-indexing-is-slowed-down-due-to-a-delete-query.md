---
title: '''ACSD-56415: Prestanda för [!UICONTROL Partial Price Indexing] fördröjd på grund av frågan "DELETE"'
description: Använd korrigeringsfilen ACSD-56415 för att åtgärda Adobe Commerce-problemet där prestandan hos [!UICONTROL Partial Price Indexing] blir långsammare på grund av en "DELETE"-fråga när databasen har många partiella prisdata att indexera.
feature: Catalog Service
role: Admin, Developer
exl-id: 0b099570-9f27-4ae2-9384-6b69ea50bd98
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-56415: Prestanda för [!UICONTROL Partial Price Indexing] är långsam på grund av `DELETE` fråga

Korrigeringen ACSD-56415 åtgärdar ett problem där prestandan hos [!UICONTROL Partial Price Indexing] blir långsammare på grund av `DELETE` fråga när databasen har många partiella prisdataindex. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 är installerat. Korrigerings-ID är ACSD-56023. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Prestanda för [!UICONTROL Partial Price Indexing] blir långsammare på grund av `DELETE` fråga när databasen har många partiella prisdataindex.

<u>Steg som ska återskapas</u>:

1. Skapa *300000 produkter* och *10 webbplatser* med den stora prestandaprofilen.
1. Logga in på Admin Panel.
1. Skapa *10 kundgrupper*.
1. Kör frågan nedan för att lägga till produkter i `_cl` tabell:

   ``
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 ``

1. Kör följande kommando för att aktivera den partiella prisindexeringsprocessen:

   ``
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 ``

<u>Förväntade resultat</u>:

SQL-frågan DELETE `main_table` FRÅN `catalog_product_index_price` körs snabbt.

<u>Faktiska resultat</u>:

SQL-frågan DELETE `main_table` FRÅN `catalog_product_index_price` utförs mycket långsamt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
