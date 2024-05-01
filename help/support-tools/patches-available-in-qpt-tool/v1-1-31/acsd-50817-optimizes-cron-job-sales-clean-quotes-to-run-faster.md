---
title: 'ACSD-50817: Optimerar sälj_ren_offerter för seriejobb för att köra snabbare'
description: Använd korrigeringsfilen ACSD-50817 för att optimera cron-jobbet "sales_clean_quotes" så att det körs snabbare genom att lägga till ett sammansatt index i kolumnerna "store_id" och "updated_at" i citattabellen.
exl-id: b08b12ff-37ac-4a7d-bce2-2a27e4f916f0
feature: Quotes
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-50817: Optimerar cron-jobb `sales_clean_quotes` att springa snabbare

Korrigeringen ACSD-50817 optimerar kronjobbet `sales_clean_quotes` för att köra snabbare genom att lägga till ett sammansatt index på `store_id` och `updated_at` kolumner i citattabellen. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.31 är installerat. Korrigerings-ID är ACSD-50817.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kronjobbet `sales_clean_quotes` är för långsam. Med den här korrigeringen har den optimerats för att köras snabbare genom att ett sammansatt index läggs till på `store_id` och `updated_at` kolumner i citattabellen.

<u>Steg som ska återskapas</u>:

1. Generera 50-80 miljoner offerter med `updated_at` anges som &lt; 30 dagars period.
1. Kör cron-jobbet `sales_clean_quotes` eller följande fråga i offerttabellen:

   ```cron
   SELECT COUNT(*) FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0')
   
   SELECT * FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0') LIMIT 50
   ```

<u>Förväntade resultat</u>

Kronjobb `sales_clean_quotes` optimeras för att köras snabbare genom att ett sammansatt index läggs till på `store_id` och `updated_at` kolumner i citattabellen.

<u>Faktiska resultat</u>

Frågan är för långsam.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
