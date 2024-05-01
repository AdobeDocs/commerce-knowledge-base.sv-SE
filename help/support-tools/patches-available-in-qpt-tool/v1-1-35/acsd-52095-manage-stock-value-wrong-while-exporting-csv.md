---
title: 'ACSD-52095: Hantera lagervärde är fel vid export av CSV'
description: Använd korrigeringsfilen ACSD-52095 för att åtgärda problemet med Adobe Commerce där produkthantering för Stock-värdet är fel vid export av CSV.
feature: Inventory, Products
role: Admin, Developer
exl-id: 9e599931-e9b1-4216-b78d-3993d9c3132d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-52095: [!UICONTROL Manage Stock] värdet är fel vid export av CSV

Korrigeringen ACSD-52095 åtgärdar ett problem där produkten `manage_stock` värdet är fel vid export av CSV. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.35 är installerat. Korrigerings-ID är ACSD-52095. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

The `manage_stock` värdet är felaktigt inställt på 0 i CSV-filen efter produktexporten.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** och ange **[!UICONTROL Manage Stock]** = *[!UICONTROL No]*.
1. Skapa en ny produkt och spara den.
1. Gå till **[!UICONTROL System]** > **[!UICONTROL Export]**.
1. Välj *[!UICONTROL Entity Type]* = *[!UICONTROL Products]* och exportera produkterna.
1. Kontrollera den genererade CSV-filen: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Återgå till **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** och ange  **[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]*.
1. Gå till **System** > **Exportera**.
Välj *[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]*.
1. Kontrollera den genererade CSV-filen: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Öppna produkten i Admin, gå till **[!UICONTROL Advanced Inventory]** och kontrollera **[!UICONTROL Manage Stock]** värde.

<u>Förväntade resultat</u>

The **[!UICONTROL Manage Stock]** värdet är *1* när det är aktiverat för produkterna.

<u>Faktiska resultat</u>

The **[!UICONTROL Manage Stock]** värdet är *0* när det är aktiverat för produkterna.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) i [!DNL Quality Patches Tool] guide.
