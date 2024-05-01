---
title: 'ACSD-53239: Inventeringsindexeraren rensar alla cacher'
description: Använd korrigeringsfilen ACSD-53239 för att åtgärda Adobe Commerce-problemet där lagerindexeraren rensar alla cacheminnen i [!UICONTROL Update on Schedule] läge.
feature: GraphQL, Inventory, Catalog Management
role: Admin, Developer
exl-id: b8e68cf7-d326-4c9e-8749-d83113de2070
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# ACSD-53239: Lagerindexeraren rensar alla cacheminnen i [!UICONTROL Update on Schedule] läge

Korrigeringen ACSD-53239 åtgärdar ett problem där lagerindexeraren rensar alla cacheminnen i [!UICONTROL Update on Schedule] läge. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36 är installerat. Korrigerings-ID är ACSD-53239. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.5-p4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Lagerindexeraren rensar alla cacheminnen i [!UICONTROL Update on Schedule] läge.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Catalog Products]** och väljer *1200* produkter.
2. Uppdatera *[!UICONTROL Qty]* till ett nytt värde och klicka på **[!UICONTROL Save]**.
3. Kör `bin/magento cron:run` direkt efter sparandet.
4. Kör följande GraphQL-fråga:

   ```GraphQL
   {
     storeConfig {
     absolute_footer
     }
   }
   ```

<u>Förväntade resultat</u>

Frågan bearbetas inom den vanliga tiden.

<u>Faktiska resultat</u>

Frågan bearbetas ovanligt långsamt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
