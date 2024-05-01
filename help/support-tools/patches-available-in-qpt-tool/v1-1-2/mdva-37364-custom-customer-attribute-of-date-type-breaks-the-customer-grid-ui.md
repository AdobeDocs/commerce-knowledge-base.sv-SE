---
title: 'MDVA-37364: Anpassat kundattribut med datumtypen avbryter stödrastergränssnittet'
description: MDVA-37364-korrigeringen löser problemet där det anpassade kundattributet av datumtyp bryter användargränssnittet för kundstödraster. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 är installerat. Patch-ID:t är MDVA-37364. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.4.
exl-id: d25baabf-45eb-403c-9f88-9c2448cc7b49
feature: Attributes, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37364: Anpassat kundattribut för datumtyp, brytningsgränssnitt för stödraster

MDVA-37364-korrigeringen löser problemet där det anpassade kundattributet av datumtyp bryter användargränssnittet för kundstödraster. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 är installerat. Patch-ID:t är MDVA-37364. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0-2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Anpassat kundattribut av datumtyp bryter användargränssnittet för kundstödraster.

<u>Steg som ska återskapas</u>:

1. Skapa ett anpassat attribut med datumtyp:
   * Gå till **Lager** > **Attribut** > **Lägg till attribut**.
   * Ställ in Indatatyp till Datum.
   * Ställ in alternativet Lägg till i kolumn till Ja.
   * Spara attributet.
1. Gå till **Administratör** > **Kunder** > **Alla kunder**.
   * Lägg till det nya anpassade attributet i rutnätet från kolumnalternativet.
1. Skapa/redigera en kund och ange värdet för det anpassade datumattributfältet som skapades.
1. Spara, indexera om och rensa cache.
1. Gå till **Kunder** > **Alla kunder**.
   * Kontrollera kundens rutnät.

<u>Förväntade resultat</u>:

Admin Customer Grid visar alla data inklusive det nya anpassade datumattributet utan att kundens gränssnitt bryts.

<u>Faktiska resultat</u>:

Gränssnittet för administratörskundstödraster är brutet.

## Tillämpa korrigeringen

Använd följande länkar beroende på vilken distributionstyp du har när du vill använda enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) -avsnitt.
