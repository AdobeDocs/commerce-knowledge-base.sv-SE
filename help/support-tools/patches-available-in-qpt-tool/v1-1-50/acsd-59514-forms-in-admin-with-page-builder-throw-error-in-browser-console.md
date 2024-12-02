---
title: 'ACSD-59514: Forms i Admin med  [!DNL Page Builder] utlöser ett fel i webbläsarkonsolen'
description: Använd ACSD-59514-korrigeringen för att åtgärda Adobe Commerce-problemet där formulär i Admin med  [!DNL Page Builder] orsakade felet [!DNL Page Builder] återgav i 5 sekunder utan att frigöra lås. i webbläsarkonsolen när formuläret har skickats och ändringarna kan inte sparas.
feature: Page Builder
role: Admin, Developer
exl-id: 4bb17d7b-9ea4-44c2-a42b-d0117e5f8f9a
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-59514: Forms i Admin med [!DNL Page Builder] orsakar ett fel i webbläsarkonsolen

Korrigeringen ACSD-59514 åtgärdar ett problem där formulären i Admin med [!DNL Page Builder] orsakade felet *[!DNL Page Builder]återgav i 5 sekunder utan att frigöra lås.* i webbläsarkonsolen när formuläret har skickats och det går inte att spara ändringarna. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 har installerats. Korrigerings-ID är ACSD-59514. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Forms i Admin med [!DNL Page Builder] orsakade felet *[!DNL Page Builder]återgav i 5 sekunder utan att frigöra lås.* i webbläsarkonsolen när formuläret har skickats och det går inte att spara ändringarna.

<u>Förutsättningar</u>:

Adobe Commerce [!DNL Page Builder]-moduler är installerade och aktiverade.

<u>Steg som ska återskapas</u>:

1. Öppna administratörspanelen och klicka på knappen [!UICONTROL Content].
1. Markera blocket och redigera blocket.
1. Ändra innehållet och klicka på [!UICONTROL Save].
1. Öppna konsolen och se felmeddelandet.

<u>Förväntade resultat</u>:

Blocket sparas.

<u>Faktiska resultat</u>:

Inläsaren slutar inte snurra och blocket sparas inte. Följande fel visas i webbläsarkonsolen:
*[!DNL Page Builder]återger i 5 sekunder utan att frigöra lås.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
