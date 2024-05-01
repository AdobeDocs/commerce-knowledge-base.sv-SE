---
title: '''ACSD-53750: Felet "Trasig pipe eller sluten anslutning" vid flertrådad katalog_product_price reindex"'
description: Använd korrigeringsfilen ACSD-53750 för att åtgärda Adobe Commerce-problemet där ett *trasigt rör eller en sluten anslutning* inträffar under omindexering av flertrådig katalog_product_price.
feature: Products
role: Admin, Developer
exl-id: afb30384-74e7-4857-9aff-8e99f5abc309
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-53750: *Avbruten pipe eller stängd anslutning* fel vid flertrådig `catalog_product_price` reindex

Korrigeringen ACSD-53750 åtgärdar ett problem där en *Avbruten pipe eller stängd anslutning* fel inträffar vid flertrådiga `catalog_product_price` indexera om. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.37 är installerat. Korrigerings-ID är ACSD-53750. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

*Avbruten pipe eller stängd anslutning* fel inträffar vid flertrådiga `catalog_product_price` indexera om.

<u>Steg som ska återskapas</u>:

1. Konfigurera RabbitMq.
1. Generera exempeldata med hjälp av bifogade `small.xml` -fil.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** och ange **[!UICONTROL Stock/Source reindex strategy]** = **[!UICONTROL Asynchronous]**.
1. Ange dimensionsläge för index som stöder det. t.ex., `catalog_product_price_website_and_customer_group` eller `customer_group`.

   ```
   bin/magento indexer:set-dimensions-mode catalog_product_price customer_group
   ```

1. Kör återställning av indexerare för `catalog_product_price`.

   ```
   bin/magento indexer:reset catalog_product_price
   ```

1. Kör indexeraren för återställningsindexeraren med flera trådar.

   ```
   MAGE_INDEXER_THREADS_COUNT=10 bin/magento indexer:reindex catalog_product_price
   ```

<u>Förväntade resultat</u>:

Inga fel inträffar.

<u>Faktiska resultat</u>:

Följande fel orsakas av en AMQP-anslutning: *Avbruten pipe eller stängd anslutning*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
