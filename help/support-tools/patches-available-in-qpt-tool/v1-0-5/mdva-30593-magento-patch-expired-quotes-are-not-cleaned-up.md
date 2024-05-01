---
title: "MDVA-30593-korrigering: utgångna citattecken rensas inte"
description: MDVA-30593-korrigeringen åtgärdar ett problem där citattecken som har upphört att gälla enligt inställningen **Offerts livstid** inte rensas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.3.4.
exl-id: 5ee91546-a5cb-4282-bdfc-c9bb3438af50
feature: Cache, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# MDVA-30593-korrigering: utgångna citattecken rensas inte

MDVA-30593-korrigeringen löser problemet där citattecken som gått ut enligt **Offertlivstid** är inte rensade. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.3.4.

## Berörda produkter och versioner

* Adobe Commerce (alla distributionsmetoder) 2.3.0-2.3.3.x

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Offerter som har gått ut enligt **Offertlivstid** är inte rensade.

<u>Steg som ska återskapas:</u>

1. Gå till Commerce Admin **Lager** > **Konfiguration** > **Försäljning** > **Utcheckning** > **Kundvagn**.
1. Ange **Offertens livstid (dagar)** = *1*
1. Spara konfiguration och rensa cache.
1. Logga in som kund.
1. Lägg en produkt i kundvagnen.
1. Efter en dag, gå tillbaka till vagnen.

<u>Förväntat resultat:</u>

Offerten är rensad och produkten tas bort från vagnen eftersom det gamla priset inte längre är giltigt.

<u>Faktiskt resultat:</u>

Produkten är fortfarande i varukorgen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
