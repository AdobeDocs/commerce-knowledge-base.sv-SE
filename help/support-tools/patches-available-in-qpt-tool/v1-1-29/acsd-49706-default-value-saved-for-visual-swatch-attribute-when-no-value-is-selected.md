---
title: 'ACSD-49706: Standardvärdet har sparats för attributet för visuell färgruta när inget värde har valts'
description: Använd korrigeringsfilen ACSD-49706 för att korrigera Adobe Commerce-problemet där ett standardvärde sparas för ett visuellt färgruteattribut när inget värde har valts.
exl-id: fe6071df-f2a4-443a-acfa-67f3d253c5e4
feature: Admin Workspace, Attributes
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-49706: Standardvärde har sparats för attributet för visuell färgruta när inget värde har valts

Korrigeringen ACSD-49706 åtgärdar ett problem där ett standardvärde sparas för ett visuellt färgruteattribut när inget värde har valts. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 är installerat. Korrigerings-ID är ACSD-49706. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett standardvärde sparas för ett visuellt färgruteattribut när inget värde är markerat.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. Klicka på **[!UICONTROL Add New Attribute]**.
1. Fyll i fälten.

   * Välj till exempel indatatyp *[!UICONTROL Visual Swatch]* och lägga till flera alternativ (till exempel *Röd*, *Grön*). Se till att du väljer något av dessa alternativ som standard.
   * Klicka på **[!UICONTROL Save Attribute]**.

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Redigera *[!UICONTROL Default]* attributuppsättning.
1. Flytta *[!UICONTROL New Attribute]* från kolumnen *[!UICONTROL Unassigned Attributes]* till *[!UICONTROL Product Details]* i mittkolumnen.

   * Klicka på **[!UICONTROL Save]**.

1. Skapa en ny produkt med *[!UICONTROL Default]* attributuppsättning.

   * Lämna *[!UICONTROL New Attribute]* tom och spara.

1. När filen har sparats visas ett värde i *[!UICONTROL New Attribute]*.

<u>Förväntade resultat</u>:

Inget värde har tilldelats *[!UICONTROL New Attribute]* som standard.

<u>Faktiska resultat</u>:

Ett standardvärde används för attributet när en produkt sparas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
