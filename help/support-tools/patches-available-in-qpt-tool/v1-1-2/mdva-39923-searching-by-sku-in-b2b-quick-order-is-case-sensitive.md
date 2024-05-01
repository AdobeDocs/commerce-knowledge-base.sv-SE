---
title: 'MDVA-39923: Sökning på SKU i B2B-snabbordningsfunktioner är skiftlägeskänslig'
description: MDVA-39923-korrigeringen åtgärdar ett problem där kunderna får ett felmeddelande när de söker igenom beställningen av SKU:n i B2B-snabborderfunktionen med ett annat fall än det som namnet sparas med. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 är installerat. Korrigerings-ID är MDVA-39923. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: 52e435df-28a7-49be-a257-7e5801601d57
feature: B2B, Catalog Management, Orders, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-39923: Sökning på SKU i B2B-snabbordningsfunktioner är skiftlägeskänsligt

MDVA-39923-korrigeringen åtgärdar ett problem där kunderna får ett felmeddelande när de söker igenom beställningen av SKU:n i B2B-snabborderfunktionen med ett annat fall än det som namnet sparas med. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 är installerat. Korrigerings-ID är MDVA-39923. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce (alla distributionsmetoder) 2.4.1-p1

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Att söka på SKU i B2B-snabbordningsfunktioner är skiftlägeskänsligt och visar ett fel när ett annat skiftläge används än det som SKU:n sparas med.

<u>Förutsättningar</u>:

B2B-moduler är installerade.

<u>Steg som ska återskapas</u>:

1. Logga in på administratören och gå till **Lager** > **Konfiguration** > **B2B**.
1. Aktivera **Delad katalog** och **Snabbordning**.
1. Skapa en produkt med SKU i versaler, t.ex. TEST20-1234
1. Tilldela skapad produkt till **Delad katalog**.
1. Logga in som kund och klicka på **Snabbordning**.
1. Ange SKU i gemener, t.ex. test20-1234.

<u>Förväntade resultat</u>:

Produkten bör hittas oavsett vilket fall som används.

<u>Faktiska resultat</u>:

Följande felmeddelande har tagits emot: *1 produkt(er) kräver din uppmärksamhet*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
