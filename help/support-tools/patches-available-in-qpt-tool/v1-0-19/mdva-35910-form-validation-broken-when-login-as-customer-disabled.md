---
title: 'MDVA-35910: Formulärvalidering fungerar inte när "Logga in som kund" är inaktiverat'
description: MDVA-35910-korrigeringen löser problemet där formulärvalideringen för att skapa kundkonto bryts när tillägget **Logga in som kund** inaktiveras. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Korrigerings-ID är MDVA-35910. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.
exl-id: fa63d725-33f0-4422-bcd5-d62dfee01b65
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-35910: Formulärvalidering fungerar inte när Inloggning som kund är inaktiverat

MDVA-35910-korrigeringen löser problemet där valideringen av skapa kundkontoformulär bryts när **Logga in som kund** tillägg är inaktiverat. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Korrigerings-ID är MDVA-35910. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce i molninfrastruktur 2.4.1

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.4.1-2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Navigera till **Lager > Konfiguration > Kunder**. Inaktivera **Logga in som kund** i Admin.
1. Under **Logga in som kund**, ange **Aktivera tillägg** = *Nej*.
1. Spara konfigurationen och tömma cachen.
1. Navigera tillbaka till butiken och klicka **Registrera** (Skapa ett kundkonto).
1. Fyll i kontoformuläret och bekräfta om valideringen under **Bekräfta e-post** fungerar eller inte.

<u>Förväntade resultat</u>:

Processen för att skapa kundkonton slutförs utan fel.

<u>Faktiska resultat</u>:

Processen för att skapa kundkonton slutförs inte, och javascript-konsolfel visas i stället.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
