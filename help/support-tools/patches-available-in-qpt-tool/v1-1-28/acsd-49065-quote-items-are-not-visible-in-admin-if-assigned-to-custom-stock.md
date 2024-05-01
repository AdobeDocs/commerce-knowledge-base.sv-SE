---
title: 'ACSD-49065: Offertobjekt visas inte i administratören'
description: Använd patchen ACSD-49065 för att åtgärda Adobe Commerce-problemet där offertobjekten inte syns i administratören om de bara tilldelats det anpassade lagret.
exl-id: 3a5ceb4c-4c94-4938-98d9-9171f2633056
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-49065: Offertobjekt visas inte i administratören

Korrigeringen ACSD-49065 åtgärdar ett problem där offertobjekten inte är synliga i administratören om de bara är tilldelade till det anpassade lagret. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 är installerat. Korrigerings-ID är ACSD-49065. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Offertobjekten visas inte i administratören om de bara är tilldelade till det anpassade arkivet.

Förutsättningar:

**[!UICONTROL B2B]** och **[!UICONTROL Inventory]** moduler måste installeras.

<u>Steg som ska återskapas</u>:

1. Aktivera **[!UICONTROL Company]** och **[!UICONTROL B2B Quote]** under **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Skapa en sekundär **[!UICONTROL Inventory Source]** och tilldela den till en sekundär **[!UICONTROL Inventory Stock]**.
1. Skapa en ny produkt genom att endast tilldela den sekundära produkten (ej standard) **[!UICONTROL Inventory Source]**.
1. Gå till butiken och skapa ett nytt företagskonto. Logga in som **[!UICONTROL Company Admin]** och lägg den skapade produkten i kundvagnen.
1. Navigera till kundvagnen och *[!UICONTROL Request a Quote]*.
1. Gå till administratören och visa den begärda offerten på **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.

<u>Förväntade resultat</u>:

Objekten visas i den nya offerten som skapats med nya produkter utan att produkterna sparas om.

<u>Faktiska resultat</u>:

The *[!UICONTROL Items Quoted]* -avsnittet är tomt. Om du sparar om den nya produkten visas objekten.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
