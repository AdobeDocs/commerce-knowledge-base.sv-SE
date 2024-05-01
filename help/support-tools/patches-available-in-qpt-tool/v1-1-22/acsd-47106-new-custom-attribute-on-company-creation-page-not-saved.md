---
title: "ACSD-47106: nytt anpassat attribut på företagsskapandesidan har inte sparats"
description: Använd korrigeringsfilen ACSD-47106 för att åtgärda Adobe Commerce-problemet där ett värde inte kan sparas i ett nytt anpassat attribut på en företagsskapelsesida.
exl-id: 941d6d8f-36eb-4b50-980f-e4afe6bf33df
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-47106: Nytt anpassat attribut på företagsskapandesidan har inte sparats

Korrigeringen ACSD-47106 åtgärdar ett problem där ett värde inte kan sparas i ett nytt anpassat attribut på en företagsskapandesida. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22 är installerat. Korrigerings-ID är ACSD-47106. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett värde kan inte sparas i ett nytt anpassat attribut på en företagsskapandesida.

<u>Förutsättningar</u>:

* B2B-moduler är installerade.

<u>Steg som ska återskapas</u>:

1. Gå till Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Customer]** > **[!UICONTROL Add New Attribute]**.
1. Skapa nytt attribut: _Test 01_.
1. Gå till Commerce Admin > **[!UICONTROL Customers]** > **[!UICONTROL Companies]** > och skapa ett nytt företag med alla detaljer som behövs.
1. Försök lägga till ett värde i det anpassade attributet _Test 01_.
1. Försök att uppdatera värdet för det anpassade attributet _Test 01_.

<u>Förväntade resultat</u>:

Ändringarna sparas.

<u>Faktiska resultat</u>:

Ändringarna sparas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
