---
title: '''ACSD-52786: Katalogregel *[!UICONTROL SKU is]* gäller för alla produkter som börjar med SKU'
description: Använd korrigeringsfilen ACSD-52786 för att åtgärda Adobe Commerce-problemet där katalogregelvillkoret är *[!UICONTROL SKU is]* gäller för alla produkter som börjar med angiven SKU.
feature: Price Rules
role: Admin
exl-id: af373b6c-5944-412b-a544-cc6fc3f209d3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-52786: Katalogregel &quot;*[!UICONTROL SKU is]*&quot; gäller för alla produkter som börjar med SKU

Korrigeringen ACSD-52786 åtgärdar ett problem där katalogregelvillkoret åtgärdas *[!UICONTROL SKU is]* gäller för alla produkter som börjar med den angivna SKU:n. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.35 är installerat. Korrigerings-ID är ACSD-52786. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Villkor för katalogregel *[!UICONTROL SKU is]* gäller för alla produkter som börjar med den angivna SKU:n.

<u>Steg som ska återskapas</u>:

1. Skapa två produkter, en med SKU &quot;24&quot; och en annan med SKU &quot;24 MB01&quot;.
1. Navigera till **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Använd följande villkor:
   * *[!UICONTROL If ** ALLA **av dessa villkor är** TRUE **]*: *[!UICONTROL SKU is 24]*
1. Ange ett rabattbelopp i funktionsmakron.
1. Klicka på **[!UICONTROL Save and Apply]**.
1. Töm cacheminnet.
1. Gå till butiken och kontrollera priset på 24 MB01.

<u>Förväntade resultat</u>:

Katalogregeln används endast för en enskild produkt med SKU 24.

<u>Faktiska resultat</u>:

Villkor för katalogregel *[!UICONTROL SKU is]* gäller för alla produkter som börjar med den angivna SKU:n.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
