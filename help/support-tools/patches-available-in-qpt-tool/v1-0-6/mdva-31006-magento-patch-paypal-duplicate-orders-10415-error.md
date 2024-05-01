---
title: 'MDVA-31006: PayPal Duplicate Orders 10415 error'
description: Korrigeringen MDVA-31006 åtgärdar ett problem där PayPal Express-betalning skapar dubblettorder med ett 10415-fel. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 är installerat. Problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: ff471fd3-f580-4149-83bc-67f6fce8e28d
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# MDVA-31006: PayPal-dubblettorder 10415-fel

Korrigeringen MDVA-31006 åtgärdar ett problem där PayPal Express-betalning skapar dubblettorder med ett 10415-fel. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 är installerat. Problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

* Adobe Commerce (alla distributionsmetoder) 2.3.2 - 2.4.0

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användaren skickas inte till Adobe Commerce ordersida, så den tomma sidan uppdateras och den andra beställningen placeras, vilket ger dubblettorder.

<u>Förutsättningar</u>:

* Adobe Commerce är installerat.
* Betalning för PayPal Express-utcheckning har konfigurerats.
* Logga in på Commerce-administratören. Gå till **Lager** > **Konfiguration** > **Försäljning** > **Betalningsmetoder** > markera **Paypal Express-utcheckning** > **Konfigurera** > **Avancerade inställningar** > **Hoppa över ordergranskningssteget** > *Nej*.

<u>Steg som ska återskapas</u>:

1. Logga in som användare.
1. Markera ett objekt och klicka på **Lägg i kundvagnen**.
1. Klicka på kundvagnen och klicka **Gå till kassan**.
1. Gå till PayPal Express-fönstret och gör en betalning.
1. Du omdirigeras till Adobe Commerce ordergranskningssida.
1. Tryck på **Montera beställning** -knappen.
1. Emulera systemfel på grund av problem med serverinfrastrukturen. Användaren ser en tom sida.
1. Uppdatera sidan.

<u>Förväntade resultat</u>:

* Kunden omdirigeras till sidan Ordergranskning och ser ett felmeddelande &quot;*En betalningstransaktion har redan slutförts. Kontrollera om ordern har lagts.*&quot;
* I payment.log, som finns i `/var/log/payment.log`, det finns ett fel 10415, men bara en order skapades.

<u>Faktiska resultat</u>:

* Eftersom kunden inte skickas till Adobe Commerce sida för lyckade beställningar, uppdateras den tomma sidan och en andra beställning läggs så att två dubblettbeställningar skapas.
* I payment.log, som finns i `/var/log/payment.log`, finns det ett fel 10415.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
