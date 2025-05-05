---
title: 'ACSD-58163: [!UICONTROL Cart Price Rule] tillämpar inte rabatt från matchande [!UICONTROL Customer Segment]-kundvagn utan kupongkod'
description: Använd patchen ACSD-58163 för att åtgärda Adobe Commerce-problemet där [!UICONTROL Cart Price Rule] inte tillämpar en rabatt för en gäst från den matchande [!UICONTROL Customer Segment]-vagnen utan kupongkod.
feature: Products
role: Admin, Developer
exl-id: bc8587be-076c-4210-902c-6ecb69f581e2
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-58163: [!UICONTROL Cart Price Rule] tillämpar inte rabatt från matchande [!UICONTROL Customer Segment]-kundvagn utan kupongkod

Korrigeringen ACSD-58163 åtgärdar ett problem där [!UICONTROL Cart Price Rule] inte tillämpar en rabatt från den matchande [!UICONTROL Customer Segment]-vagnen utan kupongkod. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 har installerats. Korrigerings-ID är ACSD-58163. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.5.0.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!UICONTROL Cart Price Rule] använder inte någon rabatt för en gäst från den matchande [!UICONTROL Customer Segment]-vagnen utan en kupongkod.

<u>Steg som ska återskapas</u>:

1. Skapa kundsegment:
   * För besökare.
   * Med villkoret att du har en produkt i kundvagnen.

1. Skapa en *[!UICONTROL Cart Price Rule]*:
   * Utan kupongkod.
   * Med villkoret att matcha besökarens kundsegment.

1. Skapa en enkel produkt.
1. Öppna butiken som gäst.
1. Lägg en enkel produkt i kundvagnen.
1. Gå till kundvagnen.

<u>Förväntade resultat</u>:

*[!UICONTROL Cart Price Rule]* rabatt används.

<u>Faktiska resultat</u>:

*[!UICONTROL Cart Price Rule]* rabatt används inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
