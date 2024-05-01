---
title: 'ACSD-49898: Produktstödrastret genererar ett undantag'
description: Använd patchen ACSD-49898 för att åtgärda problemet med Adobe Commerce där produktrutnätet genererar ett undantag när en paketerad produkt har ett specialpris som överstiger 1 000.
exl-id: 16a0ec90-7577-46ef-aeb3-a7e9658cf64b
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-49898: Produktstödrastret genererar ett undantag

Korrigeringsfilen ACSD-49898 åtgärdar ett problem där stödrastret för produkter genererar ett undantag när en paketerad produkt har ett specialpris som överstiger 1 000. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 är installerat. Korrigerings-ID är ACSD-49898. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktstödrastret genererar ett undantag när en paketerad produkt har ett specialpris som överstiger 1 000. Problemet gäller användning av kommatecken i stället för punkter för decimaltal i vissa språkområden.

<u>Steg som ska återskapas</u>:

1. Skapa en paketerad produkt.
1. Ställ in specialpriset på 9999; spara och stäng.
1. Navigera till **[!UICONTROL Catalog]** > **[!UICONTROL Products]**

>[!NOTE]
>
>Sök efter SKU för paketerad produkt om den inte syns.

<u>Förväntade resultat</u>:

* Användaren kan filtrera/se den paketerade produkten till specialpriset.
* Specialpriset anges som en procentandel för paketerade produkter och som pris för andra produkttyper.

<u>Faktiska resultat</u>:

Följande fel genereras: *Ett icke-numeriskt värde påträffades*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
