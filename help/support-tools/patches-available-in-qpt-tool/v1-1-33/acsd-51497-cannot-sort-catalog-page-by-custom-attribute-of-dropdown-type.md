---
title: 'ACSD-51497: Det går inte att sortera katalogsidan efter ett anpassat attribut av typen Listruta'
description: Använd patchen ACSD-51497 för att åtgärda Adobe Commerce-problemet där en kund inte kan sortera en katalogsida efter anpassade attribut av typen listruta.
feature: Attributes, Cache, Catalog Management, Categories
role: Developer
exl-id: 60a4f375-9b9a-4026-9dc7-d9f847a75656
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-51497: Det går inte att sortera katalogsidan efter anpassat attribut av typen *Listruta*

Korrigeringen ACSD-51497 åtgärdar ett problem där en kund inte kan sortera en katalogsida efter ett anpassat attribut av typen *Listruta*. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 är installerat. Korrigerings-ID är ACSD-51497. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En kund kan inte sortera en katalogsida efter ett anpassat attribut av typen *Listruta*.

<u>Steg som ska återskapas</u>

1. Skapa sex enkla produkter och tilldela dem till en enda kategori.
1. Skapa ett produktattribut om du vill lägga till det som ett sorteringsalternativ på listsidorna.

   * Gå till **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Add New Attribute]**.
   * I **[!UICONTROL Properties]** ställer du in följande:

      * *[!UICONTROL Default Label]* = *test*
      * *[!UICONTROL Catalog Input Type]* för butiksägare = *Listruta*
      * *[!UICONTROL Options]*:

         * *först*
         * *sekund*
         * *tredje*
         * *fjärde*

   * I **[!UICONTROL Storefront Properties]** ställer du in följande:

      * *[!UICONTROL Used for sorting in product listing]* = *Ja*
      * Lämna alla andra alternativ som *Standard*.

1. Tilldela *test* attributet till *Standard* attributuppsättning i **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Konfigurera de produkter som ska ha *test* attributvärden.

   * SKU: s00001, test: fjärde
   * SKU: s00002, test: third
   * SKU: s00003, test: sekund
   * SKU: s00004, test: first
   * SKU: s00005, test: fjärde
   * SKU: s00006, test: third

1. Indexera om och rensa cache.
1. Gå till kategorin i butiken.
1. Sortera efter *test* -attribut.

<u>Förväntade resultat</u>:

Produkterna sorteras efter *test* -attribut.

<u>Faktiska resultat</u>:

Produkterna sorteras inte efter *test* -attribut.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
