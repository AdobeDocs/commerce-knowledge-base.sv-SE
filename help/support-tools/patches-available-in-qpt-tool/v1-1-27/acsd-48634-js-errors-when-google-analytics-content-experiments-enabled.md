---
title: '"ACSD-48634: [!DNL JS] fel när [!DNL Google Analytics Content Experiments] enabled'''
description: Använd patchen ACSD-48634 för att korrigera [!DNL JS] fel på en [!DNL staging] uppdateringssida när [!DNL Google Analytics Content Experiments] är aktiverat.
exl-id: 4a9f201d-eaf0-4e43-a1a1-0a9ffb0a2ead
feature: Catalog Management, Categories, Console, Page Content
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-48634: [!DNL JS] fel när [!DNL Google Analytics Content Experiments] aktiverad

Korrigeringsfilerna för ACSD-48634 [!DNL JS] fel på en [!DNL staging] uppdateringssida när [!DNL Google Analytics Content Experiments] är aktiverat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 är installerat. Korrigerings-ID är ACSD-48634. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!DNL JS] fel inträffar på en [!DNL staging] uppdateringssida när [!DNL Google Analytics Content Experiments] är aktiverat.

<u>Steg som ska återskapas</u>:

1. I **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**, skapa ytterligare en webbplats, lagra och **[!UICONTROL Store View]**. Se till att **[!UICONTROL Store View]** är *[!UICONTROL Enabled]*.
1. Konfigurera **[!DNL Configure Google Analytics]** genom att **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**:
   * För **[!DNL Main]** och ytterligare webbplatser [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Google Tag Manager]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Container Id]**: *[!UICONTROL (GTM container ID)]*
      * **[!DNL Uncheck]** *[!UICONTROL Use Default]* för andra fält, men ändra dem inte.
   * För **[!DNL Default Config]** [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Universal Analytics]*
      * **[!UICONTROL Account Number]**: *[!UICONTROL (Universal Analytics account number)]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
1. Inaktivera **[!DNL Configure Google Analytics]** på **[!DNL Default Config]** [!DNL scope] genom att ändra **[!UICONTROL Enable]** från *[!UICONTROL Yes]* till *[!UICONTROL No]*. Se till att inte ändra någonting annat!
1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Skapa och redigera **[!UICONTROL category]** och lägga till en schemalagd uppdatering:
   * Alla namn, startdatum i framtiden, slutdatum i framtiden och eventuella ändringar i **[!UICONTROL category]** ([!UICONTROL For Example]: *[!UICONTROL disable category]*).
1. Spara uppdateringen och kontrollera [!DNL browser developer console] för fel.

<u>Förväntade resultat</u>:

Nej [!DNL JS] fel och ändringar i [!DNL staging] uppdateringen har sparats.

<u>Faktiska resultat</u>:

[!DNL JS] fel visas i konsolen, formuläret har fel format och [!DNL spinner] inaktiveras aldrig efter att du sparat.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
