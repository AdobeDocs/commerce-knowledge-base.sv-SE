---
title: 'MDVA-38132: Oändlig omdirigering när serverdelens URL inte är samma som standardwebbplatsens URL'
description: Korrigeringen MDVA-38132 åtgärdar problemet med oändlig omdirigering när serverdelens URL är en annan än standardwebbplatsens URL. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 är installerat. Korrigerings-ID är MDVA-38132. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.
exl-id: 122145d7-0961-47f8-8ab6-a15d62996e49
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-38132: Oändlig omdirigering när serverdelens URL är en annan än standardwebbplatsens URL

Korrigeringen MDVA-38132 åtgärdar problemet med oändlig omdirigering när serverdelens URL är en annan än standardwebbplatsens URL. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 är installerat. Korrigerings-ID är MDVA-38132. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**
Adobe Commerce om molninfrastruktur 2.3.4-p2

**Kompatibel med Adobe Commerce:**
Adobe Commerce (alla distributionsmetoder) 2.3.3-2.4.2-p1
>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

På Commerce Admin-panelen finns en oändlig omdirigering när serverdelens URL är en annan än standardwebbplatsens URL.

<u>Förutsättningar</u>:

* Bas-URL används både för backend och storefront. Bas säker URL används inte.
* Webbservern är konfigurerad så att Adobe Commerce kan nås via två olika URL:er. URL1 används för installation av Adobe Commerce.

<u>Steg som ska återskapas</u>:

1. Gå till administrationspanelen > **Lager** > **Konfiguration** > **Webb**.
1. Lämna ursprunglig bas-URL i global konfiguration. Det är din URL1.
1. Växla till huvudwebbplatsens omfattning.
1. Ändra bas-URL:en till en annan URL (se villkoren för att konfigurera webbservern korrekt). Detta är din URL2.
1. Rensa cacheminnet (om det är nödvändigt och möjligt).
1. Öppna administrationspanelen.

<u>Förväntade resultat</u>:

Administrationspanelen har öppnats och kan navigeras. Huvudwebbplatsens butik har öppnats och kan navigeras.

<u>Faktiska resultat</u>:

Oändlig omdirigering sker. Adobe Commerce dirigerar om från URL1 till URL2 och fortsätter fram och tillbaka.

## Tillämpa korrigeringen

Använd följande länkar beroende på vilken Adobe Commerce-produkt du använder för att tillämpa enskilda patchar:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som finns i QPT-verktyget finns i [Patchar tillgängliga i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
