---
title: 'ACSD-56790: **[!UICONTROL move out of stock to bottom]** fungerar inte när du sorterar produkter i  [!DNL Visual Merchandiser]'
description: Använd patchen ACSD-56790 för att åtgärda Adobe Commerce-problemet där alternativet för att gå från lager till botten inte fungerar när du sorterar produkter i Visual Merchandiser.
feature: Products, Categories
role: Admin, Developer
exl-id: a0c61696-a12d-4c1a-a061-e2f17f38e1f4
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# ACSD-56790: **[!UICONTROL move out of stock to bottom]** fungerar inte när du sorterar produkter i [!DNL Visual Merchandiser]

Korrigeringen ACSD-56790 åtgärdar ett problem där alternativet att gå från lager till botten inte fungerar när du sorterar produkter i [!DNL Visual Merchandiser]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 är installerat. Korrigerings-ID är ACSD-56790. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

The **[!UICONTROL move out of stock to bottom]** fungerar inte när du sorterar produkter i [!DNL Visual Merchandiser]

<u>Steg som ska återskapas</u>:

1. Installera Adobe Commerce.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** och skapa följande attribut.
1. Skapa en ny webbplats: **Icke-main**.
1. Skapa en **Icke-huvudbutik** på denna nya webbplats.
1. Skapa två butiker:

   * Först i **Main website Store**.
   * Andra i **Icke-huvudbutik**.

1. Skapa två källor:
   * Bokstäver.
   * Nummer.

1. Skapa två lager:
   * Första huvud - försäljningskanaler: Huvudwebbplats - tilldelade källor: Bokstäver.
   * Andra icke-huvudkanaler - försäljningskanaler: Icke-huvudtilldelade källor: Nummer.

1. Skapa tre enkla produkter på båda webbplatserna, i kategorin Standard, som alla är tilldelade till båda källorna:

   * ProduktA - kvantitet *10* antal bokstäver *0* i siffror.
   * Produkt1 - kvantitet *0* antal bokstäver *10* i siffror.
   * ProduktA1 - kvantitet *10* antal bokstäver *10* i siffror.

1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** och markera  **[!UICONTROL Default category]**.
1. Ändra omfånget till **Första**.
1. Expandera Produkter i avsnittet Kategori.
1. Välj sorteringsordning som: **[!UICONTROL move out of stock to bottom]**

<u>Förväntade resultat</u>:

Listan över produkterna med **lagerutfall** produkterna flyttas längst ned.

<u>Faktiska resultat</u>:

Produkterna läses inte in. En sida dirigeras om till admin-kontrollpanelen med felmeddelandet: `Invalid security or form key. Please refresh the page`

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
