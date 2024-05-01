---
title: 'MDVA-40311: Felet "Ogiltig säkerhet eller formulärnyckel" efter inloggning i Admin om anpassad administratörssökväg har konfigurerats'
description: 'Korrigeringen MDVA-40311 åtgärdar ett fel där administratörsanvändaren får ett felmeddelande: *Ogiltig säkerhet eller formulärnyckel. Uppdatera sidan* efter inloggning i administratören om den anpassade administratörssökvägen är konfigurerad och den hemliga nyckeln är aktiverad. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 är installerat. Korrigerings-ID är MDVA-40311. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4."'
exl-id: d4562f09-0aed-438e-8c2e-90557aa2f146
feature: Admin Workspace, Compliance, Security
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-40311: Felet &quot;Ogiltig säkerhet eller formulärnyckel&quot; efter inloggning i Admin om anpassad administratörssökväg har konfigurerats

MDVA-40311-korrigeringen åtgärdar ett problem där administratörsanvändaren får ett felmeddelande: *Ogiltig säkerhets- eller formulärnyckel. Uppdatera sidan*, efter inloggning i Admin om den anpassade administratörssökvägen är konfigurerad och den hemliga nyckeln är aktiverad. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 är installerat. Korrigerings-ID är MDVA-40311. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörsanvändaren får ett felmeddelande: *Ogiltig säkerhets- eller formulärnyckel. Uppdatera sidan*, efter inloggning i Admin om den anpassade administratörssökvägen är konfigurerad och den hemliga nyckeln är aktiverad.

<u>Steg som ska återskapas</u>:

* Logga in som Admin-användare med ett giltigt användarnamn och lösenord.

<u>Förväntade resultat</u>:

Användaren kan logga in utan något felmeddelande.

<u>Faktiska resultat</u>:

*Ogiltig säkerhets- eller formulärnyckel. Uppdatera sidan* felmeddelande visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
