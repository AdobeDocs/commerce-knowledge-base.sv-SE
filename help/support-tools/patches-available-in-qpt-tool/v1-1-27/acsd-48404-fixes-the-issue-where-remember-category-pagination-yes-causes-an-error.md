---
title: "ACSD-48404: *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* orsakar fel när användaren trycker på bakåtknappen i webbläsaren"
description: Åtgärda Adobe Commerce-problemet med korrigeringen ACSD-48404 där *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* orsakar ett fel när användaren trycker på webbläsarens bakåtknapp.
exl-id: b4b96198-dee6-4b3c-b60a-0983ef8ef7b2
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-48404: *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* orsakar fel när webbläsarens knapp trycks ned

Korrigeringen ACSD-48404 åtgärdar ett problem där *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* orsakar ett fel när användaren trycker på webbläsarens bakåtknapp. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 är installerat. Korrigerings-ID är ACSD-48404. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

*[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* orsakar ett fel när användaren trycker på webbläsarens bakåtknapp.


<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]** och ange *[!UICONTROL Remember Category Pagination]* till *Ja*.
1. Öppna en kategori i butiken.
1. Välj ett värde som inte är standardvärdet i *[!UICONTROL Show Per Page]* nedrullningsbar meny. När du har valt ett alternativ läses sidan in igen.
1. När sidan har lästs in på nytt klickar du på en produkt på katalogsidan.
1. På den öppnade produktinformationssidan klickar du på **[!UICONTROL Back]** webbläsarknappen.

<u>Förväntade resultat</u>:

Katalogsidan öppnas igen.

<u>Faktiska resultat</u>:

Kategorisidan returnerar ett fel.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
