---
title: "ACSD-47079: Produkternas lagerstatus uppdateras inte när delproduktens lagerstatus ändras"
description: Använd patchen ACSD-47079 för att åtgärda Adobe Commerce-problemet där sammansatta produkter (bundle, grouped och configurable) inte uppdateras när delproduktens lagerstatus ändras via REST API-POSTEN /rest/V1/layer/source-items.
exl-id: 603e4548-fb04-43b4-a033-4f2c7f665fae
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-47079: Produkternas lagerstatus uppdateras inte när delproduktens lagerstatus ändras

Korrigeringen ACSD-47079 åtgärdar ett problem där lagerstatus för sammansatta produkter (bundle, grouped och configurable) inte uppdateras när delproduktens lagerstatus ändras via REST API-POST `/rest/V1/inventory/source-items`. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 är installerat. Korrigerings-ID är ACSD-47079. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Lagerstatus för sammansatta produkter (bundle, grouped och configurable) uppdateras inte när delproduktens Stock-status ändras via REST API-POST `/rest/V1/inventory/source-items`.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar, paketerad och grupperad produkt med en enkel underordnad produkt för varje.
1. Ange varje enkel underordnad produktstatus till **[!UICONTROL Out of Stock]** med `source-items` API-anrop.
1. Kontrollera nu den överordnade produktens lagerstatus.

<u>Förväntade resultat</u>:

Den överordnade produktens status är [!UICONTROL Out of Stock].

<u>Faktiska resultat</u>:

Den överordnade produktens status är [!UICONTROL In Stock].

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
