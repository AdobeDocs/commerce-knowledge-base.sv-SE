---
title: '"ACSD-50895: [!DNL Google Analytics] 3 GTM-taggar aktiveras inte om [!DNL Google Analytics] 4 GTM är inte konfigurerat'
description: Åtgärda Adobe Commerce-problemet med korrigeringen ACSD-50895 där [!DNL Google Analytics] 3 GTM-taggar aktiveras inte om [!DNL Google Analytics] 4 GTM är inte konfigurerat.
role: Admin
exl-id: da48f6f1-a68b-4a9c-a79a-d7bd01b65dc2
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-50895: [!DNL Google Analytics] 3 GTM-taggar aktiveras inte om [!DNL Google Analytics] 4 GTM är inte konfigurerat

Korrigeringen ACSD-50895 åtgärdar ett problem där [!DNL Google Analytics] 3 GTM-taggar aktiveras inte om [!DNL Google Analytics] 4 GTM är inte konfigurerat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 är installerat. Korrigerings-ID är ACSD-50895. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!DNL Google Analytics] 3 GTM-taggar aktiveras inte om [!DNL Google Analytics] 4 GTM är inte konfigurerat.

<u>Steg som ska återskapas</u>:

1. Logga in som administratör.
1. Aktivera **[!DNL Google Analytics 3]** och **[!DNL Google Tag Manager]** in **Administratör** > **Butik** > **Konfiguration** > **Försäljning** > **GOOGLE API** > **Google Analytics**.
1. Aktivera inte **[!DNL Google Analytics 4]** och **[!DNL Google Tag Manager]**.
1. Öppna produktsidan på Storefront.

<u>Förväntade resultat</u>:

GTM-taggarna utlöses bara när **[!DNL Google Analytics]** 3 GTM är aktiverat.

<u>Faktiska resultat</u>:

GTM-taggarna utlöses inte när **[!DNL Google Analytics]** 4 GTM är inaktiverat.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
