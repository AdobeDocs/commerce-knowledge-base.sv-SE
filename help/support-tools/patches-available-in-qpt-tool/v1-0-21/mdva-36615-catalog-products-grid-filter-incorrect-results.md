---
title: 'MDVA-36615: Felaktiga resultat för katalogproduktrutnätsfilter'
description: Korrigeringen MDVA-36615 åtgärdar problemet med felaktigt antal produkter i administratörens produktrutnät. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 är installerat. Korrigerings-ID är MDVA-36615. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.
exl-id: 7ed70753-c637-4c13-8290-aa5e8a4d1b65
feature: Catalog Management, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# MDVA-36615: Felaktiga resultat för katalogproduktrutnätsfilter

Korrigeringen MDVA-36615 åtgärdar problemet med felaktigt antal produkter i administratörens produktrutnät. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 är installerat. Korrigerings-ID är MDVA-36615. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce i molninfrastruktur 2.4.2

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Felaktigt produktantal i administratörens produktrutnät.

<u>Steg som ska återskapas:</u>

1. Skapa enkla och konfigurerbara produkter med samma fras i namnet (t.ex.&quot;röd skjorta&quot;/&quot;röd skjorta&quot;).
1. På *Administratör* sidebar, gå till **Katalog** > **Produkter** > sök efter den här frasen.
1. Klicka **Filter**. Ange typ till *Konfigurerbar produkt*.
1. Klicka **Använd filter**.

<u>Faktiskt resultat:</u>

Korrekt nummer i matchad produkträknare.

<u>Förväntat resultat:</u>

Felaktigt nummer i matchad produkträknare.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
