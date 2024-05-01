---
title: "ACSD-51700: Fel vid växling av butiksvyer på nedladdningsbar produktredigeringssida"
description: Använd patchen ACSD-51700 för att åtgärda Adobe Commerce-problemet när ett fel inträffar när butiksvyer växlas på en nedladdningsbar produktredigeringssida i administratören.
feature: Products
role: Admin
exl-id: 652876a5-275d-437f-9cb3-baf4e7b23aae
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51700: Fel vid växling av butiksvyer på hämtningsbar produktredigeringssida

Korrigeringen ACSD-51700 åtgärdar ett problem där ett fel inträffar när butiksvyer växlas på en hämtningsbar produktredigeringssida i administratören. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.33 är installerat. Korrigerings-ID är ACSD-51700. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p1

## Problem

Ett fel inträffar när butiksvyer växlas på en nedladdningsbar produktredigeringssida i administratören.

<u>Steg som ska återskapas</u>:

1. Skapa en nedladdningsbar produkt med ett namn [!DNL SKU]och priset. Lägg inte till några länkar och spara produkten.
1. Växla från alla butiksvyer till standardbutiksvyn.
1. Skapa en länk för den hämtningsbara produkten och spara den.
1. Växla från standardbutiksvyn till alla butiksvyer.

<u>Förväntade resultat</u>:

De länkade produkterna visas.

<u>Faktiska resultat</u>:

Följande fel visas:

*Föråldrad funktionalitet: number_format(): Om null skickas till parametern #1 ($num) av typen float används inte vendor/magento/module-downloadable/Ui/DataProvider/Product/Form/Modifier/Data/Links.php på rad 228*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
