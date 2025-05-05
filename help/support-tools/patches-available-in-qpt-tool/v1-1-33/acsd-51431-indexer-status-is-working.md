---
title: 'ACSD-51431: Indexerstatus är *[!UICONTROL Working]* även om det inte finns några poster i ändringsloggen'
description: Använd korrigeringen ACSD-51431 för att åtgärda Adobe Commerce-problemet där indexerarstatusen är *[!UICONTROL Working]* trots att det inte finns några poster i ändringsloggen.
feature: Logs, Price Indexer
role: Admin
exl-id: 85977b78-7f6b-47c7-b33e-16668bdf98fe
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-51431: Indexerarstatusen är *[!UICONTROL Working]* trots att det inte finns några poster i ändringsloggen

Korrigeringen ACSD-51431 åtgärdar prestandaproblemet där indexerarstatusen är *[!UICONTROL Working]* trots att det inte finns några poster i ändringsloggen. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.33 har installerats. Korrigerings-ID är ACSD-51431. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Indexerarstatusen är *[!UICONTROL Working]* trots att det inte finns några poster i ändringsloggen.

<u>Steg som ska återskapas</u>:

1. Ange **[!UICONTROL indexers]** till [!UICONTROL Update on Schedule].
1. Konfigurera kronijobbet så att det körs varje minut.
1. Spara ändringar i olika produkter samtidigt.
1. Kör `bin/magento indexer:status` om några minuter.

<u>Förväntade resultat</u>:

Ändringarna bearbetas och indexerarna har statusen *[!UICONTROL Ready]*. Status *[!UICONTROL Schedule]* är *[!UICONTROL idle (0 in the backlog)]*.

<u>Faktiska resultat</u>:

Ändringarna bearbetas och indexerarna har statusen *[!UICONTROL Ready]*. Status *[!UICONTROL Schedule]* visar dock *[!UICONTROL working (0 in the backlog)]*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
