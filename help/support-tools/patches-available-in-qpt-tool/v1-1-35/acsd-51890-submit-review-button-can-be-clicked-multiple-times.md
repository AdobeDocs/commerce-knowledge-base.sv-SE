---
title: 'ACSD-51890: Knappen [!UICONTROL Submit review] kan klickas flera gånger'
description: Använd korrigeringsfilen ACSD-51890 för att åtgärda Adobe Commerce-problemet där användaren kan klicka på knappen [!UICONTROL Submit Review] flera gånger utan att behöva  [!DNL Google reCAPTCHA v3] validera.
feature: Products
role: Admin
exl-id: f6369a24-24bd-4e5e-a870-a13f507ada94
source-git-commit: 7dbf9a796fe2026b0657b719d10e5bb21b964fb6
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51890: Knappen **[!UICONTROL Submit Review]** kan klickas flera gånger utan **[!DNL Google reCAPTCHA v3]**-validering

>[!NOTE]
>
>Den här korrigeringen har ersatts av [ACSD-55112](/help/support-tools/patches-available-in-qpt-tool/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md).

Korrigeringen ACSD-51890 åtgärdar ett problem där knappen **[!UICONTROL Submit Review]** kan klickas flera gånger utan **[!DNL Google reCAPTCHA v3]**-validering. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 har installerats. Korrigerings-ID är ACSD-51890. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Knappen **[!UICONTROL Submit Review]** kan klickas flera gånger utan **[!DNL Google reCAPTCHA v3]**-validering.

<u>Steg som ska återskapas</u>:

1. Aktivera **[!DNL Google reCAPTCHA v3]** för produktgranskningen.
1. Öppna produktsidan och gå till avsnittet **[!UICONTROL Review]** och kontrollera att [!DNL reCAPTCHA] är synlig.
1. Fyll i granskningsformuläret och klicka på knappen **[!UICONTROL Submit Review]** flera gånger så snabbt som möjligt.
1. Öppna avsnittet **[!UICONTROL Review]** från administratören.

<u>Förväntade resultat</u>

Dubblettgranskningar skapas inte.

<u>Faktiska resultat</u>

Dubblettgranskningar skapas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) i [!DNL Quality Patches Tool]-handboken.
