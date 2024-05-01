---
title: "MDVA-33704-korrigering: Butiksupphämtning visas inte"
description: MDVA-33704-korrigeringen åtgärdar ett problem där produkter med alternativ för hämtning i butik inte visas som leveranssätt.
exl-id: 2c5c7627-5d2e-44d2-9579-314dbd31ee8b
feature: Shipping/Delivery
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# MDVA-33704-korrigering: Butiksupphämtning visas inte

MDVA-33704-korrigeringen åtgärdar ett problem där produkter med alternativ för hämtning i butik inte visas som leveranssätt.

Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Patch-ID:t är MDVA-33704. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:** Adobe Commerce i molninfrastruktur 2.4.0-p1

**Kompatibel med Adobe Commerce:** Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.4.0-2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Förutsättning</u>:<br>

**Plocka i butik** aktiverad

<u>Steg som ska återskapas</u>:

1. Lägg en produkt i kundvagnen.
1. Gå till kassan.
1. Lägg till leveransinformation och välj en annan leveransmetod än att hämta i butiken.
1. Välj **Fortsätt till betalning**, men gå sedan inte vidare till betalningssidan.
1. Gå tillbaka till **Kontakt och leverans** -avsnitt.
1. Välj **Upphämtning**.
1. Välj **Butik** och **Klicka för att betala**.
1. Observera att din leveransadress automatiskt anges som faktureringsadress.
1. Uppdatera webbsidan.

<u>Förväntade resultat</u>:

Upphämtningsalternativet i butiken visas som en leveransmetod, som förväntat.

<u>Faktiska resultat</u>:

Alternativet för hämtning i butik visas inte som en leveransmetod.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som finns i QPT-verktyget finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
