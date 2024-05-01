---
title: 'ACSD-52148: Administratörsinloggningen för Google v3 reCAPTCHA misslyckas ibland'
description: Använd patchen ACSD-52148 för att åtgärda Adobe Commerce-problemet där administratörsinloggningen för Google v3 reCAPTCHA ibland misslyckas.
feature: Admin Workspace
role: Admin
exl-id: ebebd8e6-a75a-4d4f-aeb8-ca924ff92c94
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-52148: Administratörsinloggningen för Google v3 reCAPTCHA misslyckas ibland

Korrigeringen ACSD-52148 åtgärdar ett problem där administratörsinloggningen för Google v3 reCAPTCHA ibland misslyckas. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.33 är installerat. Korrigerings-ID är ACSD-52148. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Inloggning av administratörer för Google v3 reCAPTCHA misslyckas ibland.

<u>Steg som ska återskapas</u>:

1. Aktivera Google v3 reCAPTCHA för administratörsinloggningen.
1. Logga in på Admin och skicka captcha.

<u>Förväntade resultat</u>

Administratören har loggats in.

<u>Faktiska resultat</u>

* *reCAPTCHA-verifieringen misslyckades.* fel visas då och då.
* Ett fel har loggats:

  ```
  report.ERROR: Can not resolve reCAPTCHA parameter. {"exception":"[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)"} []
  ```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
