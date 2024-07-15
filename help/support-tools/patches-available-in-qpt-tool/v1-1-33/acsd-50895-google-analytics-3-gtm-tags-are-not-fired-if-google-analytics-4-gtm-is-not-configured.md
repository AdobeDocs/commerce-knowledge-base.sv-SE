---
title: 'ACSD-50895: [!DNL Google Analytics] 3 GTM-taggar utlöses inte om [!DNL Google Analytics] 4 GTM inte har konfigurerats'
description: Använd ACSD-50895-korrigeringen för att åtgärda Adobe Commerce-problemet där  [!DNL Google Analytics] 3 GTM-taggar inte utlöses om  [!DNL Google Analytics] 4 GTM inte har konfigurerats.
role: Admin
exl-id: da48f6f1-a68b-4a9c-a79a-d7bd01b65dc2
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-50895: [!DNL Google Analytics] 3 GTM-taggar utlöses inte om [!DNL Google Analytics] 4 GTM inte har konfigurerats

ACSD-50895-korrigeringen åtgärdar ett problem där [!DNL Google Analytics] 3 GTM-taggar inte utlöses om [!DNL Google Analytics] 4 GTM inte är konfigurerad. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 har installerats. Korrigerings-ID är ACSD-50895. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!DNL Google Analytics] 3 GTM-taggar utlöses inte om [!DNL Google Analytics] 4 GTM inte har konfigurerats.

<u>Steg som ska återskapas</u>:

1. Logga in som administratör.
1. Aktivera **[!DNL Google Analytics 3]** och **[!DNL Google Tag Manager]** i **Admin** > **Store** > **Configuration** > **Sales** > **Google API** > **Google Analytics**.
1. Aktivera inte **[!DNL Google Analytics 4]** och **[!DNL Google Tag Manager]**.
1. Öppna produktsidan på Storefront.

<u>Förväntade resultat</u>:

GTM-taggarna utlöses när endast **[!DNL Google Analytics]** 3 GTM är aktiverat.

<u>Faktiska resultat</u>:

GTM-taggarna utlöses inte när **[!DNL Google Analytics]** 4 GTM är inaktiverat.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
