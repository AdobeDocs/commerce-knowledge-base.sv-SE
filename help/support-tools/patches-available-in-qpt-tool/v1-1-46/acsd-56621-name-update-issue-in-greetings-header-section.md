---
title: 'ACSD-56621: Uppdaterade namn visas inte i sidhuvudet för hälsningar för företagsadministratörsanvändare'
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

Korrigeringsfilen ACSD-56621 åtgärdar ett problem där det uppdaterade förnamnet och efternamnet för företagsadministratörsanvändaren inte återspeglas i sidhuvudet för hälsningar. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 har installerats. Korrigerings-ID är ACSD-56621. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

De uppdaterade namnen visas inte i sidhuvudet för hälsningar för företagsadministratörer.

<u>Steg som ska återskapas</u>:

1. Navigera till panelen **[!UICONTROL Admin]**.
1. Gå till **[!UICONTROL Stores]** och välj **[!UICONTROL Configuration]**.
1. Under avsnittet **[!UICONTROL General]** väljer du **[!UICONTROL B2B]** för att aktivera B2B-företagsfunktioner.
1. Gå till **[!UICONTROL Storefront]** och registrera ett nytt företag.
1. Logga in som företagsadministratör.
1. Gå till **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** och ändra för- och efternamnsfälten efter behov.

<u>Förväntade resultat</u>:

Användarens för- och efternamn i sidhuvudet för hälsningar ändras omedelbart.

<u>Faktiska resultat</u>:

Användarens för- och efternamn ändras bara när användaren loggar ut och loggar in igen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
