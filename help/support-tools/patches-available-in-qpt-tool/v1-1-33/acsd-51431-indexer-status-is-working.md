---
title: 'ACSD-51431: Indexerstatus är *[!UICONTROL Working]* trots att det inte finns några poster i ändringsloggen'
description: Använd korrigeringsfilen ACSD-51431 för att åtgärda Adobe Commerce-problemet där indexerarstatusen är *[!UICONTROL Working]* trots att det inte finns några poster i ändringsloggen.
feature: Logs, Price Indexer
role: Admin
exl-id: 85977b78-7f6b-47c7-b33e-16668bdf98fe
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-51431: Indexerarstatus är *[!UICONTROL Working]* även om det inte finns några poster i ändringsloggen

Korrigeringen ACSD-51431 åtgärdar prestandaproblemet där indexerarstatusen är *[!UICONTROL Working]* även om det inte finns några poster i ändringsloggen. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.33 är installerat. Korrigerings-ID är ACSD-51431. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Indexerarens status är *[!UICONTROL Working]* även om det inte finns några poster i ändringsloggen.

<u>Steg som ska återskapas</u>:

1. Ange **[!UICONTROL indexers]** till [!UICONTROL Update on Schedule].
1. Konfigurera kronijobbet så att det körs varje minut.
1. Spara ändringar i olika produkter samtidigt.
1. Kör `bin/magento indexer:status` om några minuter.

<u>Förväntade resultat</u>:

Ändringarna bearbetas och indexerarna finns i *[!UICONTROL Ready]* status. The *[!UICONTROL Schedule]* status är *[!UICONTROL idle (0 in the backlog)]*.

<u>Faktiska resultat</u>:

Ändringarna bearbetas och indexerarna finns i *[!UICONTROL Ready]* status. Men *[!UICONTROL Schedule]* status visas *[!UICONTROL working (0 in the backlog)]*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
