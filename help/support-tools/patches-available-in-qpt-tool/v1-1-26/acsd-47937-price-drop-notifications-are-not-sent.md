---
title: 'ACSD-47937: meddelanden om prisfall skickas inte på grund av cachelagring på programnivå'
description: Använd patchen ACSD-47937 för att åtgärda Adobe Commerce-problemet där meddelanden om prisfall inte alltid skickas på grund av cachelagring på applikationsnivå.
exl-id: f39c9ef6-4689-427f-bd61-3a52dec88be2
feature: Admin Workspace, Cache, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-47937: Meddelanden om prisfall skickas inte på grund av cachelagring på programnivå

Korrigeringen ACSD-47937 åtgärdar ett problem där meddelanden om prisfall inte alltid skickas på grund av cachelagring på applikationsnivå. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 är installerat. Korrigerings-ID är ACSD-47937. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 och 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4, 2.4.5 och 2.4.5-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kunderna får inte e-post om att produktpriserna sjunker för efterföljande produktprisändringar.

<u>Steg som ska återskapas</u>:

1. Aktivera **[!UICONTROL Product Alert]** för båda *[!UICONTROL Price Changes]* och *[!UICONTROL Back in Stock]* in **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]**.
1. Aktivera **[!UICONTROL Display Out of Stock Products]**.
1. Skapa en enkel produkt (ABC) med kvantitet = 0.
1. Skapa en kund i butiken och prenumerera på produkten ovan för att få produktmeddelanden om prisfall.
1. Starta produktvarningen för kunder.

   ```PHP
   bin/magento queue:consumers:start product_alert
   ```

1. Sänk priset för ABC-produkten.
1. Utlös produktvarningen cron.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Sänk priset på ABC-produkten igen.
1. Utlös produktvarningen cron.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

>[!NOTE]
>
>Om du inte känner till [!DNL n98] kan du köra `bin/magento cron:run command` som vanligt och övervaka `cron_schedule` tabell för att säkerställa `catalog_product_alert` jobbet får status som lyckat.

<u>Förväntade resultat</u>:

Den andra prissänkningen skickas.

<u>Faktiska resultat</u>:

Den andra prissänkningen skickas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
