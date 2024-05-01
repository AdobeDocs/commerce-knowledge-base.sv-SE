---
title: 'ACSD-44591: Fel vid beställning utan CAPTCHA-bekräftelse'
description: Korrigeringen ACSD-44591 löser problemet där användaren får felmeddelanden när han eller hon försöker göra en beställning utan CAPTCHA-bekräftelse.
exl-id: 5459aa14-dcba-474d-aafa-e4cc73daafbc
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-44591: Fel vid beställning utan CAPTCHA-bekräftelse

Korrigeringen ACSD-44591 löser problemet där användaren får felmeddelanden när han eller hon försöker göra en beställning utan CAPTCHA-bekräftelse.
Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 är installerat. Korrigerings-ID är ACSD-44591. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användaren får felmeddelanden när han eller hon försöker göra en beställning utan CAPTCHA-bekräftelse.

<u>Steg som ska återskapas</u>:

1. Konfigurera Google ReCaptcha v2 (jag är ingen robot).
1. Aktivera ReCaptcha för utcheckning.
1. Försök att göra en beställning utan att klicka på knappen ReCaptcha.
1. När du fått felmeddelandet om att ReCaptcha saknas (*ReCaptcha-validering misslyckades, försök igen*), klicka på **ReCaptcha** och försök sedan beställa.

<u>Förväntade resultat</u>:

Ordningen kommer inte att placeras med felaktig ReCaptcha.

<u>Faktiska resultat</u>:

Du får följande fel:

* *ReCaptcha-validering misslyckades, försök igen*
* *Ingen sådan kundvagn med ID = 1*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
