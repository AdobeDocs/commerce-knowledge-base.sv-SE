---
title: 'Alternativet ''ACSD-56790: **[!UICONTROL move out of stock to bottom]*** fungerar inte när du sorterar produkter i  [!DNL Visual Merchandiser]'
description: Använd patchen ACSD-56790 för att åtgärda Adobe Commerce-problemet där alternativet för att gå från lager till botten inte fungerar när du sorterar produkter i Visual Merchandiser.
feature: Products, Categories
role: Admin, Developer
exl-id: a0c61696-a12d-4c1a-a061-e2f17f38e1f4
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# ACSD-56790: Alternativet **[!UICONTROL move out of stock to bottom]** fungerar inte när du sorterar produkter i [!DNL Visual Merchandiser]

Korrigeringen ACSD-56790 åtgärdar ett problem där alternativet att flytta från lager till underkant inte fungerar när du sorterar produkter i [!DNL Visual Merchandiser]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 har installerats. Korrigerings-ID är ACSD-56790. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Alternativet **[!UICONTROL move out of stock to bottom]** fungerar inte när du sorterar produkter i [!DNL Visual Merchandiser]

<u>Steg som ska återskapas</u>:

1. Installera Adobe Commerce.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** och skapa följande attribut.
1. Skapa en ny webbplats: **Icke-huvudwebbplats**.
1. Skapa ett **icke-huvudarkiv** på den nya webbplatsen.
1. Skapa två butiker:

   * Först i **huvudwebbplatsarkivet**.
   * Sekund i **icke-huvudarkivet**.

1. Skapa två källor:
   * Bokstäver.
   * Nummer.

1. Skapa två lager:
   * Första huvud - försäljningskanaler: Huvudwebbplats - tilldelade källor: Bokstäver.
   * Andra icke-huvudkanaler - försäljningskanaler: Icke-huvudtilldelade källor: Nummer.

1. Skapa tre enkla produkter på båda webbplatserna, i kategorin Standard, som alla är tilldelade till båda källorna:

   * ProduktA - kvantitet *10* i bokstäver, kvantitet *0* i siffror.
   * Produkt1 - Antal *0* i bokstäver, Antal *10* i siffror.
   * ProduktA1 - kvantitet *10* i bokstäver, kvantitet *10* i siffror.

1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** och välj **[!UICONTROL Default category]**.
1. Ändra omfattningen till **Första**.
1. Expandera Produkter i avsnittet Kategori.
1. Välj sorteringsordningen som: **[!UICONTROL move out of stock to bottom]**

<u>Förväntade resultat</u>:

Listan över produkter med **färdiga**-produkter flyttas längst ned.

<u>Faktiska resultat</u>:

Produkterna läses inte in. En sida dirigeras om till admin-kontrollpanelen med felmeddelandet: `Invalid security or form key. Please refresh the page`

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
