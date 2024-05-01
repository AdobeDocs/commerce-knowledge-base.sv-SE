---
title: 'ACSD-56621: Uppdaterade namn visas inte i hethubriken för företagsadministratörer'
description: Använd patchen ACSD-56621 för att åtgärda Adobe Commerce-problemet där det uppdaterade förnamnet och efternamnet för företagsadministratörsanvändaren inte visas i sidhuvudet för hälsningar.
feature: Companies, B2B, User Account
role: Admin, Developer
exl-id: 4ad9c878-b617-4e6a-939c-be15faf7124b
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-56621: Uppdaterade namn visas inte i sidhuvudet för hälsningar för företagsadministratörsanvändare

Korrigeringsfilen ACSD-56621 åtgärdar ett problem där det uppdaterade förnamnet och efternamnet för företagsadministratörsanvändaren inte återspeglas i sidhuvudet för hälsningar. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 är installerat. Korrigerings-ID är ACSD-56621. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

De uppdaterade namnen visas inte i sidhuvudet för hälsningar för företagsadministratörer.

<u>Steg som ska återskapas</u>:

1. Navigera till **[!UICONTROL Admin]** -panelen.
1. Gå till **[!UICONTROL Stores]** och markera **[!UICONTROL Configuration]**.
1. Under **[!UICONTROL General]** avsnitt, markera **[!UICONTROL B2B]** för att aktivera funktioner för B2B-företag.
1. Gå till **[!UICONTROL Storefront]** och registrera ett nytt företag.
1. Logga in som företagsadministratör.
1. Gå till **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** och ändra för- och efternamnsfälten efter behov.

<u>Förväntade resultat</u>:

Användarens för- och efternamn i sidhuvudet för hälsningar ändras omedelbart.

<u>Faktiska resultat</u>:

Användarens för- och efternamn ändras bara när användaren loggar ut och loggar in igen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
