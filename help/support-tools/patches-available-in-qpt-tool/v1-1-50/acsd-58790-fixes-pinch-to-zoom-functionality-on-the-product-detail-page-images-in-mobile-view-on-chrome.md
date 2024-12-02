---
title: 'ACSD-58790: Åtgärdar funktionen att fästa vid zoomning på produktinformationssidans bilder i mobilvyn på  [!DNL Chrome]'
description: ACSD-58790 åtgärdar ett Adobe Commerce-problem där bilden i mobilvyn på  [!DNL Chrome] inte zoomade in bilden som förväntat.
feature: Storefront
role: Admin, Developer
exl-id: 0985534c-49af-439a-8859-39222dedcf67
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-58790: Åtgärdar funktionen att fästa vid zoomning på produktinformationssidans bilder i mobilvyn på [!DNL Chrome]

Korrigeringen ACSD-58790 åtgärdar ett Adobe Commerce-problem där bilden i mobilvyn på [!DNL Chrome] inte zoomade in på bilden som förväntat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 har installerats. Korrigerings-ID är ACSD-58790. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Åtgärdar funktionen att fästa till zoomning på produktinformationssidans bilder i mobilvyn på [!DNL Chrome].

<u>Steg som ska återskapas</u>:

1. Skapa en produkt med en bild.
1. Öppna produkten från en [!DNL Chrome]-webbläsare.
1. Klicka på bilden och kontrollera att bilden zoomas vid dubbelklickning.
1. Växla till mobilvyn med hjälp av utvecklarverktygen för [!DNL Chrome].
1. Klicka på bilden.
1. Dubbeltryck.

<u>Förväntade resultat</u>:

Bilden zoomas in när du dubbelklickar på den.

<u>Faktiska resultat</u>:

Bilden zoomas inte in när du dubbelklickar på den. Problemet är specifikt för [!DNL Chrome] i mobilvyn eftersom zoomfunktionen fungerar som förväntat i [!DNL Firefox].

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
