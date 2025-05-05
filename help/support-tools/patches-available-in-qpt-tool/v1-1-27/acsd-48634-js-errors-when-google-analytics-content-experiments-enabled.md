---
title: 'ACSD-48634: [!DNL JS] fel när [!DNL Google Analytics Content Experiments] är aktiverat'
description: Använd korrigeringen ACSD-48634 för att korrigera [!DNL JS] fel på en [!DNL staging] uppdateringssida när [!DNL Google Analytics Content Experiments] är aktiverat.
exl-id: 4a9f201d-eaf0-4e43-a1a1-0a9ffb0a2ead
feature: Catalog Management, Categories, Console, Page Content
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-48634: [!DNL JS] fel när [!DNL Google Analytics Content Experiments] är aktiverat

ACSD-48634-korrigeringen åtgärdar [!DNL JS] fel på en [!DNL staging]-uppdateringssida när [!DNL Google Analytics Content Experiments] är aktiverat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 har installerats. Korrigerings-ID är ACSD-48634. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!DNL JS] fel inträffar på en [!DNL staging]-uppdateringssida när [!DNL Google Analytics Content Experiments] är aktiverat.

<u>Steg som ska återskapas</u>:

1. Skapa ytterligare en webbplats, butik och **[!UICONTROL Store View]** i **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**. Kontrollera att **[!UICONTROL Store View]** är *[!UICONTROL Enabled]*.
1. Konfigurera **[!DNL Configure Google Analytics]** genom att gå till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**:
   * För **[!DNL Main]** och andra webbplatser [!DNL scope]:
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
1. Skapa och redigera alla **[!UICONTROL category]** och lägg till en schemalagd uppdatering:
   * Alla namn, startdatum i framtiden, slutdatum i framtiden och ändringar i **[!UICONTROL category]** ([!UICONTROL For Example]: *[!UICONTROL disable category]*).
1. Spara uppdateringen och kontrollera om det finns fel i [!DNL browser developer console].

<u>Förväntade resultat</u>:

Inga [!DNL JS]-fel och ändringarna av [!DNL staging]-uppdateringen har sparats.

<u>Faktiska resultat</u>:

[!DNL JS] fel visas i konsolen, formuläret har fel format och [!DNL spinner] inaktiveras aldrig efter att filen har sparats.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
