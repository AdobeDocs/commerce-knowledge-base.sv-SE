---
title: "ACSD-52736: [!UICONTROL Cart Price Rule] fungerar inte som förväntat"
description: Använd patchen ACSD-52736 för att åtgärda Adobe Commerce-problemet där en [!UICONTROL Cart Price Rule] som innehåller kraven för konfigurerbar produktkvantitet inte fungerar som förväntat.
feature: Shopping Cart, Products
role: Admin, Developer
exl-id: 8403b418-b197-4695-88a8-e322b18cd4ad
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-52736: [!UICONTROL Cart Price Rule] fungerar inte som förväntat

Korrigeringen ACSD-52736 åtgärdar ett fel där en [!UICONTROL Cart Price Rule] som innehåller kraven för konfigurerbar produktkvantitet inte fungerar som förväntat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36 har installerats. Korrigerings-ID är ACSD-52736. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En [!UICONTROL Cart Price Rule] som innehåller kraven för konfigurerbar produktkvantitet fungerar inte som förväntat.

<u>Steg som ska återskapas</u>:

1. Skapa en kundvagnsregel:
   * [!UICONTROL Apply] = Procent av produktprisrabatt
   * [!UICONTROL Discount Amount] = 60
   * [!UICONTROL Maximum Qty Discount is Applied to] = 1
   * [!UICONTROL Discount Qty Step (Buy X)] = 1
   * Använd regeln endast för varukorgsartiklar som matchar följande villkor: Kvantitet i kundvagn är 1
2. Lägg en produkt med [!UICONTROL Qty] = 2 i kundvagnen.
3. Kontrollera kundvagnspriserna.

<u>Förväntade resultat</u>:

Regeln tillämpas inte eftersom kvantiteten produkter i vagnen är *2*.

<u>Faktiska resultat</u>:

Rabatten tillämpas.

<u> Ytterligare steg krävs efter korrigeringsinstallationen</u>:

När korrigeringen har tillämpats måste kundvagnsregelvillkoren som använder attributet *Quantity* tas bort och läggas till igen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
