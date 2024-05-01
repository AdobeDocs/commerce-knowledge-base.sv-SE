---
title: 'ACSD-52160: Produktvalideringsresultat mot kundprisregeln'
description: Använd patchen ACSD-52160 för att åtgärda Adobe Commerce-problemet där produktvalideringsresultatet mot kundprisregeln inte utvärderas korrekt baserat på regelvillkoret *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*.
exl-id: a371c539-4440-4c84-baa4-774c32f66e41
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-52160: Produktvalideringsresultatet mot kundprisregeln utvärderas inte korrekt

Korrigeringen ACSD-52160 åtgärdar ett problem där produktvalideringsresultatet mot kundvagnsprisregeln inte utvärderas korrekt baserat på regelvillkoret *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 är installerat. Korrigerings-ID är ACSD-52160. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktvalideringsresultatet mot kundvagnsprisregeln utvärderas inte korrekt baserat på regelvillkoret *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*.

<u>Steg som ska återskapas</u>:

1. Skapa två produkter som har tilldelats två olika kategorier.
1. Skapa en **[!UICONTROL Cart Price Rule]** med villkor som:

   * **SKU 1** i *[!UICONTROL FOUND]* parameter
   * **SKU 2** i *[!UICONTROL NOT FOUND]* parameter

1. Lägg båda produkterna i kundvagnen.
1. Använd kupongkoden.

<u>Förväntade resultat</u>

Kupongkoden tillämpas inte eftersom vagnen innehåller produkter från den begränsade kategorin.

<u>Faktiska resultat</u>

Kupongkoden tillämpas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) i [!DNL Quality Patches Tool] guide.
