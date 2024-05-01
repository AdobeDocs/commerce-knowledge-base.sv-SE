---
title: 'MDVA-37916: Avancerade PayPal-betalningar återgår inte till bekräftelsesidan'
description: MDVA-37916-kvalitetskorrigeringen för Adobe Commerce åtgärdar ett problem med Avancerade PayPal-betalningar som inte återgår till bekräftelsesidan efter betalning. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 är installerat. Korrigerings-ID är MDVA-37916. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: 18d7bb1c-d73a-43f6-90a8-650290dfd114
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# MDVA-37916: Avancerade PayPal-betalningar återgår inte till bekräftelsesidan

MDVA-37916-kvalitetskorrigeringen för Adobe Commerce åtgärdar ett problem med Avancerade PayPal-betalningar som inte återgår till bekräftelsesidan efter betalning. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 är installerat. Korrigerings-ID är MDVA-37916. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**
Adobe Commerce om molninfrastruktur 2.3.6-p1

**Kompatibel med Adobe Commerce:**
Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.6-2.4.2-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kunden dirigeras inte till sidan Betalningsbekräftelse efter betalning när du använder metoden Avancerat för PayPal-betalningar.

<u>Steg som ska återskapas</u>: [Screencast](https://assets.adobe.com/public/025d479b-5796-4772-6f3d-adc86306a799)

1. Lägg produkten i kundvagnen och navigera till betalningssteget på kassasidan.
1. Välj **Kreditkort (Avancerat betalningsflöde)** betalningsalternativ.
1. Klicka **Fortsätt** för att öppna iframe med betalningsformuläret.
1. Fyll i betalningsformuläret med kreditkortsinformation för sandlådan.
   * Kortnummer: 4444 333 222 111 eller 4111 111 111 1111 111
   * Förfallodatum: 23/12
   * CSC: 123
1. Klicka **Betala nu**.

<u>Förväntade resultat</u>:

När betalningen har bearbetats och slutförts omdirigeras du till sidan Orderbekräftelse.

<u>Faktiska resultat</u>:

* Du omdirigeras INTE till sidan Orderbekräftelse.
* Men ordern har skapats i Adobe Commerce.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html)

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar i vår kunskapsbas finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Mer information om andra korrigeringsfiler som finns i QPT-verktyget finns i [Patchar tillgängliga i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) i vår kunskapsbas för support.
