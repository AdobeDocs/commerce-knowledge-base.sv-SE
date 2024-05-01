---
title: "ACSD-48293: sammansatta produkter ur lager vid försäljning av underordnade produkter som återköpts"
description: Använd patchen ACSD-48293 för att åtgärda Adobe Commerce-problemet där de sammansatta produkterna hamnar utanför lagret när de utsålda underordnade produkterna skickas tillbaka till lagret.
exl-id: 74ca34fe-e015-4daf-a608-4756c8ab3558
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-48293: Sammansatta produkter som inte ingår i lager när de säljs ut i underprodukter som återställs

Korrigeringen ACSD-48293 åtgärdar ett problem där de sammansatta produkterna hamnar utanför lagret när de utsålda underordnade produkterna skickas tillbaka till lagret. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 är installerat. Korrigerings-ID är ACSD-48293. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Sammansatta produkter går ut ur lager när de underordnade produkterna som sålts returneras till lager.

<u>Steg som ska återskapas</u>:

1. Skapa en sekundär webbplats-, butiks- och butiksvy.
1. Skapa två källor och resurser och tilldela dem till varje webbplats.
1. Aktivera alternativet Visa färdiga produkter under **[!UICONTROL Store]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** > **[!UICONTROL Display Out-of-Stock Products]** = *[!UICONTROL Yes]*.
1. Skapa en konfigurerbar produkt med en associerad produkt med hjälp av den primära webbplatsens Stock-källa (ange kvantitet = 1).
1. Gör en beställning av den konfigurerbara produkten.
1. Kör kronen.
1. Öppna den konfigurerbara produkten från butiken och bekräfta att den inte är i lager.
1. Öppna den konfigurerbara produkten från [!UICONTROL Admin] och ange **[!UICONTROL Manage Stock Option]** till *[!UICONTROL No]*.
1. Kör kronen.
1. Leverera beställningen och lägg till kvantitet till den enkla produkt som lagrar den.
1. Kör kronen.
1. Kontrollera produkttillgängligheten i butiken.

<u>Förväntade resultat</u>:

Den konfigurerbara produkten finns i lager.

<u>Faktiska resultat</u>:

Den konfigurerbara produkten är inte i lager.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
