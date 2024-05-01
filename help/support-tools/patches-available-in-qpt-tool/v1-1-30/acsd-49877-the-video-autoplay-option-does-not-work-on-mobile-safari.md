---
title: 'ACSD-49877: Automatisk uppspelning av video fungerar inte på mobilen [!DNL Safari]'
description: Använd korrigeringsfilen ACSD-49877 för att åtgärda Adobe Commerce-problemet där alternativet för automatisk uppspelning av video inte fungerar på mobilen [!DNL Safari] när videon är länkad direkt till en fjärrvideofil.
exl-id: 454f7cec-29b9-485b-93be-2a4f2eb77da7
feature: CMS
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-49877: Automatisk uppspelning av video fungerar inte på mobila enheter [!DNL Safari]

ACSD-49877 åtgärdar ett problem där alternativet för automatisk uppspelning på mobilen [!DNL Safari] fungerar inte när videon är länkad direkt till en fjärrvideofil. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 är installerat. Korrigerings-ID är ACSD-49877. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du [!magento/quality-patches] till den senaste versionen och kontrollera kompatibiliteten för [[!DNL Quality Patches Tool]: Sök efter patchar]. Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Automatisk uppspelning av video fungerar inte på mobilen [!DNL Safari] när videon är länkad direkt till en fjärrvideofil och inte till en direktuppspelningstjänst.

<u>Förutsättningar</u>:
[!DNL Page Builder] -moduler installeras.

<u>Steg som ska återskapas</u>:

1. Skapa en ny CMS-sida och redigera **[!UICONTROL Content Value]** med [!DNL Page Builder].
1. Lägg till en *Tabb* -element i innehållet och lägga till *Videoelement* innanför *Tabb*.
1. Klicka nu på kugghjulsknappen för att redigera *Videoelement*.
1. Lägga till en länk till en mp4-videofil i [!UICONTROL Video URL] fält.
1. Markera **[!UICONTROL Autoplay]** fält som *Ja*.
1. Klicka på **[!UICONTROL Save]**.
1. Öppna den nyligen skapade sidan på [!DNL Safari] med en iPhone.

<u>Förväntade resultat</u>

Alternativet Spela upp automatiskt fungerar på [!DNL Safari] med en iPhone.

<u>Faktiska resultat</u>

Alternativet för automatisk uppspelning fungerar inte på [!DNL Safari] med en iPhone.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
