---
title: 'ACSD-47520: kunderna förlorar belöningspoäng när en kreditnota skapas'
description: Använd patchen ACSD-47520 för att åtgärda Adobe Commerce-problemet där kunderna förlorar belöningspoäng när en kreditnota skapas.
exl-id: 748b4e05-981d-49f6-a4f5-b121d57085f4
feature: Admin Workspace, Cache, Orders, Rewards, Returns
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47520: kunderna förlorar belöningspoäng när en kreditnota skapas

Korrigeringen ACSD-47520 åtgärdar ett problem där kunderna förlorar belöningspoäng när en kreditnota skapas. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 är installerat. Korrigerings-ID är ACSD-47520. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**
* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce:**
* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5-p4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kunderna förlorar belöningspoäng när en kreditnota skapas.

<u>Steg som ska återskapas</u>:

1. Gå till Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward Points]**.
1. Ändra inställningen:
   * **[!UICONTROL Enable Reward Points Functionality]** = _Ja_
   * **[!UICONTROL Enable Reward Points Functionality on Storefront]** = _Ja_
   * **[!UICONTROL Customers May See Reward Points History]** = _Ja_
   * **[!UICONTROL Refund Reward Points Automatically]** = _Nej_
   * **[!UICONTROL Deduct Reward Points from Refund Amount Automatically]** = _Ja_
1. Gå till Admin > **[!UICONTROL Store]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** och klicka på **[!UICONTROL Add New Rate]**.
1. Lägg till ny frekvens (1:1) och tömma cachen.
1. Skapa en kund och lägg till 10 belöningspoäng på det här kontot.
1. Gå till Admin > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]** > Välj kunden som skapades i föregående steg.
1. Välj en produkt vars pris är högre än belöningspoängen.
1. Lägg en order via valfri betalningsmetod och belöningspoäng.
1. Skapa en faktura för ordern.
1. Skapa en kreditnota, men återbetala inte belöningspoängen.

<u>Förväntade resultat</u>:

* Administratören kan återbetala belöningspoängen.

* Orderstatusen stängs.

<u>Faktiska resultat</u>:

* Det finns inget sätt att återbetala belöningspoängen.

* Orderstatusen är **[!UICONTROL Completed]**.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
