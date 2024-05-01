---
title: "ACSD-52736: [!UICONTROL Cart Price Rule] fungerar inte som förväntat"
description: Använd korrigeringsfilen ACSD-52736 för att åtgärda Adobe Commerce-problemet där en [!UICONTROL Cart Price Rule] som innehåller kraven för konfigurerbar produktkvantitet fungerar inte som förväntat.
feature: Shopping Cart, Products
role: Admin, Developer
exl-id: 8403b418-b197-4695-88a8-e322b18cd4ad
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-52736: [!UICONTROL Cart Price Rule] fungerar inte som förväntat

Korrigeringen ACSD-52736 åtgärdar ett problem där en [!UICONTROL Cart Price Rule] som innehåller kraven för konfigurerbar produktkvantitet fungerar inte som förväntat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36 är installerat. Korrigerings-ID är ACSD-52736. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

A [!UICONTROL Cart Price Rule] som innehåller kraven för konfigurerbar produktkvantitet fungerar inte som förväntat.

<u>Steg som ska återskapas</u>:

1. Skapa en kundvagnsregel:
   * [!UICONTROL Apply] = Procent av produktprisrabatt
   * [!UICONTROL Discount Amount] = 60
   * [!UICONTROL Maximum Qty Discount is Applied to] = 1
   * [!UICONTROL Discount Qty Step (Buy X)] = 1
   * Använd regeln endast för varukorgsartiklar som matchar följande villkor: Kvantitet i kundvagn är 1
2. Lägg till en produkt med [!UICONTROL Qty] = 2, i kundvagnen.
3. Kontrollera kundvagnspriserna.

<u>Förväntade resultat</u>:

Regeln tillämpas inte eftersom kvantiteten produkter i vagnen är *2*.

<u>Faktiska resultat</u>:

Rabatten tillämpas.

<u> Ytterligare steg krävs efter installationen av korrigeringsfilen</u>:

När du har använt korrigeringen används villkoren för kundvagnsregeln med *Kvantitet* attributet måste tas bort och läggas till igen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
