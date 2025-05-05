---
title: '"ACSD-56415: [!UICONTROL Partial Price Indexing]-prestandan är långsam på grund av frågan "DELETE"'
description: Använd korrigeringsfilen ACSD-56415 för att åtgärda Adobe Commerce-problemet där prestandan för [!UICONTROL Partial Price Indexing] försämras på grund av en "DELETE"-fråga när databasen har många partiella prisdata att indexera.
feature: Catalog Service
role: Admin, Developer
exl-id: 0b099570-9f27-4ae2-9384-6b69ea50bd98
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-56415: Prestanda för [!UICONTROL Partial Price Indexing] har försämrats på grund av frågan `DELETE`

Korrigeringen ACSD-56415 åtgärdar ett problem där prestandan för [!UICONTROL Partial Price Indexing] försämras på grund av en `DELETE`-fråga när databasen har många partiella prisdataindex. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 har installerats. Korrigerings-ID är ACSD-56023. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Prestandan för [!UICONTROL Partial Price Indexing] försämras på grund av en `DELETE`-fråga när databasen har många partiella prisdataindex.

<u>Steg som ska återskapas</u>:

1. Skapa *300000 produkter* och *10 webbplatser* med den stora prestandaprofilen.
1. Logga in på Admin Panel.
1. Skapa *10 kundgrupper*.
1. Kör frågan nedan om du vill lägga till produkter i tabellen `_cl`:

   &grave;&grave;
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 &grave;&grave;

1. Kör följande kommando för att aktivera den partiella prisindexeringsprocessen:

   &grave;&grave;
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 &grave;&grave;

<u>Förväntade resultat</u>:

SQL-frågan DELETE `main_table` FROM `catalog_product_index_price` körs snabbt.

<u>Faktiska resultat</u>:

SQL-frågan DELETE `main_table` FROM `catalog_product_index_price` körs mycket långsamt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
