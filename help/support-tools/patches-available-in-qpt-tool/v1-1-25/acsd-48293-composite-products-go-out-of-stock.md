---
title: 'ACSD-48293: Sammansatta produkter som inte ingår i lager när de säljs ut i underprodukter som återställs'
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

Korrigeringen ACSD-48293 åtgärdar ett problem där de sammansatta produkterna hamnar utanför lagret när de utsålda underordnade produkterna skickas tillbaka till lagret. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 har installerats. Korrigerings-ID är ACSD-48293. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Sammansatta produkter går ut ur lager när de underordnade produkterna som sålts returneras till lager.

<u>Steg som ska återskapas</u>:

1. Skapa en sekundär webbplats-, butiks- och butiksvy.
1. Skapa två källor och resurser och tilldela dem till varje webbplats.
1. Aktivera alternativet för att visa färdiga produkter under **[!UICONTROL Store]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** > **[!UICONTROL Display Out-of-Stock Products]** = *[!UICONTROL Yes]*.
1. Skapa en konfigurerbar produkt med en associerad produkt med hjälp av den primära webbplatsens Stock-källa (ange kvantitet = 1).
1. Gör en beställning av den konfigurerbara produkten.
1. Kör kronen.
1. Öppna den konfigurerbara produkten från butiken och bekräfta att den inte är i lager.
1. Öppna den konfigurerbara produkten från [!UICONTROL Admin] och ställ in **[!UICONTROL Manage Stock Option]** på *[!UICONTROL No]*.
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

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
