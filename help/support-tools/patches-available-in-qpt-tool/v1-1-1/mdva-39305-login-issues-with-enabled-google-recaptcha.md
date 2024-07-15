---
title: 'MDVA-39305: Inloggningsproblem med aktiverad Google reCAPTCHA'
description: MDVA-39305-korrigeringen åtgärdar ett problem där registrerade kunder inte kan logga in med aktiverad Google reCAPTCHA. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 är installerat. Korrigerings-ID är MDVA-39305. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.4 och 2.4.7.
exl-id: 1e8e7dc7-f8f1-4432-90f4-dc73d85f353a
feature: Console
role: Admin
source-git-commit: d48abbf3ecc19a78ee1d86a12d9c32cba17d53e5
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# MDVA-39305: Inloggningsproblem med aktiverad Google reCAPTCHA

MDVA-39305-korrigeringen åtgärdar ett problem där registrerade kunder inte kan logga in med aktiverad Google reCAPTCHA. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 har installerats. Korrigerings-ID är MDVA-39305. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.4 och 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce om molninfrastruktur 2.4.2-p1, 2.4.3-p3, 2.4.5-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1-p1 - 2.4.3-p3, 2.4.4-p1 - 2.4.4-p5, 2.4.5 - 2.4.6-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Registrerade kunder kan inte logga in med den aktiverade Google reCAPTCHA.

<u>Steg som ska återskapas</u>:

1. Gå till **Store** > **Configuration** > **Security** > **Google reCAPTCHA Storefront** och aktivera **Google reCAPTCHA**.
1. Gå till **Frontend**.
1. Öppna **Developer Tool Console** i webbläsaren.

<u>Förväntade resultat</u>:

Inga CSP-varningar i konsolen.

<u>Faktiska resultat</u>:

CSP-varningar i konsolen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
