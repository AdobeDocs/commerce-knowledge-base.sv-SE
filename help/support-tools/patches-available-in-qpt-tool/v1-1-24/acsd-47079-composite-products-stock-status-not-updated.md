---
title: 'ACSD-47079: Produkternas lagerstatus uppdateras inte när delproduktens lagerstatus ändras'
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

Korrigeringen ACSD-47079 åtgärdar ett problem där Stock-statusen för sammansatta produkter (bundle, grouped och configurable) inte uppdateras när delproduktens Stock-status ändras via REST API-POSTEN `/rest/V1/inventory/source-items`. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 har installerats. Korrigerings-ID är ACSD-47079. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Lagerstatus för sammansatta produkter (bundle, grouped och configurable) uppdateras inte när delproduktens Stock-status ändras via REST API-POSTEN `/rest/V1/inventory/source-items`.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar, paketerad och grupperad produkt med en enkel underordnad produkt för varje.
1. Ange varje enkel underordnad produktstatus till **[!UICONTROL Out of Stock]** med API-anropet `source-items`.
1. Kontrollera nu den överordnade produktens lagerstatus.

<u>Förväntade resultat</u>:

Den överordnade produktens status är [!UICONTROL Out of Stock].

<u>Faktiska resultat</u>:

Den överordnade produktens status är [!UICONTROL In Stock].

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
