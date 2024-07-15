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

# ACSD-53750: *Avbruten pipe eller stängd anslutning* fel vid flertrådig indexering av `catalog_product_price`

Korrigeringen ACSD-53750 åtgärdar ett problem där ett *trasigt rör eller en stängd anslutning* inträffar vid omindexering av flertrådiga `catalog_product_price` . Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.37 har installerats. Korrigerings-ID är ACSD-53750. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

*Ett fel med bruten pipe eller stängd anslutning* inträffar under omindexering av flertrådiga `catalog_product_price`.

<u>Steg som ska återskapas</u>:

1. Konfigurera RabbitMq.
1. Generera exempeldata med den bifogade `small.xml`-filen.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** och ange **[!UICONTROL Stock/Source reindex strategy]** = **[!UICONTROL Asynchronous]**.
1. Ange dimensionsläge för index som stöder det. Exempel: `catalog_product_price_website_and_customer_group` eller `customer_group`.

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

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
