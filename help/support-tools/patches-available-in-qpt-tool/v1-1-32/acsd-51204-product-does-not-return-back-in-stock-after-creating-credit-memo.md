---
title: 'ACSD-51204: Produkten returneras inte i lager när kreditnotan har skapats'
description: Använd korrigeringsfilen ACSD-51204 för att åtgärda problemet med Adobe Commerce där produkten inte finns i lager när kreditnotan har skapats.
feature: Orders, Products, Returns
role: Admin
exl-id: 302033bc-2ca5-40d6-b692-24ae46b21c31
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-51204: Produkten returneras inte i lager när kreditnotan har skapats

Korrigeringen ACSD-51204 åtgärdar ett problem där produkten inte återgår i lager efter att kreditnotan har skapats. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 är installerat. Korrigerings-ID är ACSD-51204. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Den utsålda produkten returneras inte i lager när kreditnotan har skapats.

<u>Steg som ska återskapas</u>:

1. Installera **[!UICONTROL Adobe Commerce]** och aktivera **[!UICONTROL Inventory Management Module]** med standard *källa* och *stock* endast.
1. Lägg till en **[!UICONTROL new product]** med en kvantitet *10*.
1. Tilldela produkten till **[!UICONTROL default stock]**.
1. Lägg produkten i varukorgen i butiken och beställ 10 för hela den tillgängliga kvantiteten.
1. Generera en *faktura* och *försändelse* för ordern.
1. Skapa en **[!UICONTROL Credit Memo]** med *återgå till lager* markerad kryssruta för alla objekt.
1. Kontrollera produktens **[!UICONTROL Salable Quantity]** i Admin.

<u>Förväntade resultat</u>:

Den säljbara kvantiteten av produkten måste returneras till *10*.

<u>Faktiska resultat</u>:

Produktens säljbara kvantitet lämnas som *0*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) i [!DNL Quality Patches Tool] guide.
