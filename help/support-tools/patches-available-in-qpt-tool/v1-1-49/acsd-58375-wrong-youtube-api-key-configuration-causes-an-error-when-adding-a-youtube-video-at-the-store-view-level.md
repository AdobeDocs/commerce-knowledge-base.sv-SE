---
title: 'ACSD-58375: Felaktigt konfigurerad YouTube API-nyckel orsakar fel när video läggs till på butiksvynivå'
description: Använd patchen ACSD-58375 för att åtgärda Adobe Commerce-problemet där fel YouTube API-nyckelkonfiguration orsakar ett fel när en YouTube-video läggs till på butiksvynivå.
feature: Catalog Management, Configuration
role: Admin, Developer
exl-id: e97f53a1-930b-417f-bd1a-8084bb168d68
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-58735: Felaktigt konfigurerad YouTube API-nyckel orsakar fel när video läggs till på butiksvynivå

Korrigeringen ACSD-58735 åtgärdar ett problem där fel YouTube API-nyckelkonfiguration orsakar ett fel när en YouTube-video läggs till på butiksvynivå. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 har installerats. Patch-ID:t är ACSD-58735. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p7

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Fel YouTube API-nyckelkonfiguration orsakar ett fel när en YouTube-video läggs till på butiksvynivå.

<u>Steg som ska återskapas</u>:

1. Gå till Admin > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Video]**.
1. Ändra nivån *Scope* till *[!UICONTROL Main Website]*.
1. Lägg till API-nyckeln för YouTube.
1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Välj en produkt och bläddra till *[!UICONTROL Images and Video]*. Klicka på **[!UICONTROL Add Video]**.
1. Kopiera en YouTube-videolänk och klistra in den i videolänkfältet. Gå ut från fältet.

<u>Förväntade resultat</u>:

YouTube API-nyckeln har ett globalt omfång och är dold på webbplatsnivå.

<u>Faktiska resultat</u>:

Följande fel inträffar: *Video visas inte på grund av följande orsak: API-nyckeln är inte giltig. Skicka en giltig API-nyckel*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
