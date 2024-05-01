---
title: 'MDVA-39711: Det går inte att komma åt kundstödrastret efter att webbplatsen har tagits bort'
description: Korrigeringen MDVA-39711 åtgärdar ett problem där administratörsanvändaren inte kan komma åt kundens rutnät efter att webbplatsen har tagits bort. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 är installerat. Korrigerings-ID är MDVA-39711. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.
exl-id: 46bef304-9360-4b69-b064-631725de381c
feature: Configuration
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-39711: Det går inte att komma åt kundstödrastret efter att webbplatsen har tagits bort

Korrigeringen MDVA-39711 åtgärdar ett problem där administratörsanvändaren inte kan komma åt kundens rutnät efter att webbplatsen har tagits bort. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 är installerat. Korrigerings-ID är MDVA-39711. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7-p2, 2.3.4-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörsanvändaren kan inte komma åt kundens rutnät efter att webbplatsen har tagits bort.

<u>Steg som ska återskapas</u>:

1. Skapa en ny webbplats, butik och butiksvy.
1. Skapa en ny kund på Admin och koppla den till den skapade webbplatsen.
1. Gå till **Lager** > **Alla butiker** och ta bort den skapade webbplatsen.
1. Gå till **Kunder** > **Alla kunder**.

<u>Förväntade resultat</u>:

* Det finns inget felmeddelande.
* Alla kunder visas i rutnätet.

<u>Faktiska resultat</u>:

* Användaren får ett felmeddelande: *Det gick inte att hitta webbplatsen med ID 2 som begärdes. Verifiera webbplatsen och försök igen*
* Alla kunder visas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
