---
title: '"ACSD-51890: [!UICONTROL Submit review] kan klickas flera gånger'
description: Använd korrigeringsfilen ACSD-51890 för att åtgärda Adobe Commerce-problemet där [!UICONTROL Submit Review] kan klickas flera gånger utan [!DNL Google reCAPTCHA v3] validering.
feature: Products
role: Admin
exl-id: f6369a24-24bd-4e5e-a870-a13f507ada94
source-git-commit: 7dbf9a796fe2026b0657b719d10e5bb21b964fb6
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51890: **[!UICONTROL Submit Review]** kan klickas flera gånger utan **[!DNL Google reCAPTCHA v3]** validering

>[!NOTE]
>
>Den här korrigeringen har ersatts med [ACSD-55112](/help/support-tools/patches-available-in-qpt-tool/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md).

Korrigeringen ACSD-51890 åtgärdar ett problem där **[!UICONTROL Submit Review]** kan klickas flera gånger utan **[!DNL Google reCAPTCHA v3]** validering. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 är installerat. Korrigerings-ID är ACSD-51890. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

The **[!UICONTROL Submit Review]** kan klickas flera gånger utan **[!DNL Google reCAPTCHA v3]** validering.

<u>Steg som ska återskapas</u>:

1. Aktivera **[!DNL Google reCAPTCHA v3]** för produktrecensionen.
1. Öppna produktsidan och gå till **[!UICONTROL Review]** -avsnittet och kontrollera att [!DNL reCAPTCHA] är synlig.
1. Fyll i granskningsformuläret och klicka på **[!UICONTROL Submit Review]** knapp flera gånger så snabbt som möjligt.
1. Öppna **[!UICONTROL Review]** från Admin.

<u>Förväntade resultat</u>

Dubblettgranskningar skapas inte.

<u>Faktiska resultat</u>

Dubblettgranskningar skapas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) i [!DNL Quality Patches Tool] guide.
