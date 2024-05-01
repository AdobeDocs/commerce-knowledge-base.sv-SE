---
title: 'MDVA-29400: Dubblettbeställningar som gjorts med PayPal Express Checkout'
description: MDVA-29400-korrigeringen löser problemet där dubblettbeställningar skapas när kunderna beställer med PayPal Express Checkout. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 är installerat. Korrigerings-ID är MDVA-29400. Observera att problemet har åtgärdats i Adobe Commerce 2.4.1.
exl-id: 75b943c8-5f7c-4d94-ae92-935428fdfcf8
feature: Checkout, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-29400: Dubblettbeställningar som gjorts med PayPal Express Checkout

MDVA-29400-korrigeringen löser problemet där dubblettbeställningar skapas när kunderna beställer med PayPal Express Checkout. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 är installerat. Korrigerings-ID är MDVA-29400. Observera att problemet har åtgärdats i Adobe Commerce 2.4.1.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.3.4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Dubblettbeställningar skapas när användare gör beställningar med PayPal Express Checkout.

<u>Förutsättningar</u>:

Aktiverad och konfigurerad PayPal Express-utcheckning.

<u>Steg som ska återskapas</u>:

1. Lägg en produkt i kundvagnen.
1. Gå till utcheckningssidan och använd PayPal Express som betalningsmetod.
1. Det dirigeras om till betalande/express/review/ sida.
1. Montera order. Du omdirigeras till sidan Slutfört.
1. Gå tillbaka till PayPal/express/review/ Page.
1. Klicka på **Montera beställning** -knappen.

<u>Förväntade resultat</u>:

Endast en order skapas.

<u>Faktiska resultat</u>:

Du får följande fel: *PayPal Express-utcheckningstoken finns inte* men den andra beställningen har placerats.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) -avsnitt.
