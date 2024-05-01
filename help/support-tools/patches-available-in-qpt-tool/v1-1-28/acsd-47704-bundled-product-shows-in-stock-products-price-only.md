---
title: "ACSD-47704: Paketerad produkt visar endast priset för produkter i lager"
description: Använd patchen ACSD-47704 för att åtgärda Adobe Commerce-problemet där en paketerad produkt endast visar priset på produkter i lager.
exl-id: 91fbeaf7-4bc2-49b1-a561-c3e63f193eaa
feature: Admin Workspace, Customer Service, Orders, Products
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 0%

---

# ACSD-47704: Paketerad produkt visar endast priset för produkter i lager

Korrigeringen ACSD-47704 åtgärdar ett problem där kundsegmentpriser cachas felaktigt mellan kundgrupper. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 är installerat. Korrigerings-ID är ACSD-47704. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Priset för en paketerad produkt med Dynamic Pricing aktiverat är felaktigt eftersom endast lagerförda artiklar inkluderas.

<u>Steg som ska återskapas</u>:

1. Gå till panelen Commerce Admin.
1. Gå till **[!UICONTROL CATALOG]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Bundle Product]**.
1. Ange **[UICONROL Dynamic Price]** till **[!UICONTROL Yes]**.
1. Paketobjekt:
   * Ange **[!UICONTROL Ship bundle items]** till **[!UICONTROL Together]**
   * Välj **[!UICONTROL Add Option]**
      * **[!UICONTROL Title]** = o1
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * Markera kryssrutan
      * Lägg till en enkel produkt som finns i lager, till exempel Joust Duffle Bag SKU 24-MB01. Innan du lägger till produkten bör du anteckna priset - 34 USD
   * Standardkvantitet: 1
   * Välj **[!UICONTROL Add Option]**
      * **[!UICONTROL Option Title]** = o2
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * Markera kryssrutan
      * Lägg till en enkel produkt som finns i lager, som skiljer sig från den produkt som lagts till i föregående steg, till exempel Strive Shoulder Pack 24-MB04. Innan du lägger till produkten bör du anteckna priset - 32 USD
      * Standardkvantitet: 1
1. Spara produkt.
1. Gå till butiken och leta upp den produkt som skapades i föregående steg. Notera priset - $66 (66 = 32 + 34).
För närvarande är priset på paketprodukten lika med summan av priserna för dess alternativ.
1. Gå till panelen Commerce Admin. Gå till **[!UICONTROL CATALOG]** > **[!UICONTROL Products]**.
1. Hitta en av de enkla produkter som tidigare tilldelats som ett alternativ till paketprodukten: SKU 24-MB01 och priset 34 dollar.
1. Ändra dess kvantitet till 0.
1. Spara produkten.
1. Gå till butiken och hitta paketprodukten som skapades i föregående steg. Anteckna priset - 32 dollar. Tidigare var priset 66 dollar, vilket var summan 34 dollar från SKU 24 MB01 och 32 dollar från SKU 24 MB04. Nu när 24 MB01 är slut räknas paketpriset som 32 dollar. Det är priset på den andra produkten, som är en lagerlokal option.

<u>Förväntade resultat</u>:

Priset för paketprodukter med Dynamic Pricing aktiverat beräknas konsekvent, oavsett om alternativen finns i lager eller inte.

<u>Faktiska resultat</u>:

Priset för paketprodukten med Dynamic Pricing aktiverat är felaktigt beräknat. Den tar endast hänsyn till alternativ som finns i lager, vilket resulterar i ett lägre belopp som visas än det faktiska när ett av alternativen är utanför lagret.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
