---
title: 'ACSD-53636: Normalpris visas inte på sidan [!UICONTROL Product Listing]'
description: Använd korrigeringsfilen ACSD-53636 för att korrigera Adobe Commerce-problemet där normalpriset inte visas på *[!UICONTROL Product Listing]* sidor för konfigurerbara produkter som har underordnade produkter med specialpriser.
feature: Catalog Management, Products
role: Admin, Developer
exl-id: 97b4eb64-92d1-4db1-8e5b-915b16115663
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-53636: Normalpris visas inte på sidan *[!UICONTROL Product Listing]*

Korrigeringen ACSD-53636 åtgärdar ett problem där det vanliga priset inte visas på *[!UICONTROL Product Listing]* sidor för konfigurerbara produkter som har underordnade produkter med specialpriser. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 har installerats. Korrigerings-ID är ACSD-53636. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.4-p6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Normalpriset visas inte på *[!UICONTROL Product Listing]* sidor för konfigurerbara produkter som har underordnade produkter med specialpriser.

<u>Steg som ska återskapas</u>:

1. Logga in på administratören och gå till **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** och skapa eller öppna en konfigurerbar produkt.
2. Öppna den underordnade produkten och lägg till ett specialpris för alla eller en av de underordnade produkterna och spara produkten.
3. Gå till frontend och öppna sidan **[!UICONTROL Product Detail]** för den konfigurerbara produkten. På färgrutorna för den underordnade produkten med specialpris visas *[!UICONTROL Regular price]* borttagen (förväntas).
4. Gå till frontend och öppna sidan **[!UICONTROL Product Listing]** för den konfigurerbara produkten med specialpris. Se till att det normala priset inte visas för den konfigurerbara produktfärgrutan, till skillnad från *[!UICONTROL Product Detail Page]* och andra enkla produkter.

<u>Förväntade resultat</u>:

På sidan *[!UICONTROL Product Listing]* visar den konfigurerbara produkten det normala priset för den underordnade produkten.

<u>Faktiska resultat</u>:

På sidan *[!UICONTROL Product Listing]* visar den konfigurerbara produkten inte det normala priset för den underordnade produkten.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
