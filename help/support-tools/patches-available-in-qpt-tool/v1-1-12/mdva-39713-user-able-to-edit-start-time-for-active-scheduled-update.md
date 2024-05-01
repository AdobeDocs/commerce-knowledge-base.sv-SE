---
title: 'MDVA-39713: Användaren kan redigera starttiden för aktiv schemalagd uppdatering'
description: MDVA-39713-korrigeringen åtgärdar ett problem där en användare kan redigera starttiden för en aktiv schemalagd uppdatering. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 är installerat. Korrigerings-ID är MDVA-39713. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: c7221fdb-5fc0-4179-8d4c-c9e1f0d00692
feature: CMS
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-39713: Användaren kan redigera starttiden för aktiv schemalagd uppdatering

MDVA-39713-korrigeringen åtgärdar ett problem där en användare kan redigera starttiden för en aktiv schemalagd uppdatering. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 är installerat. Korrigerings-ID är MDVA-39713. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.3.3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.3.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användaren kan redigera starttiden för en aktiv schemalagd uppdatering.

<u>Steg som ska återskapas</u>:

1. Skapa nya CMS-sidor.
1. Välj **Schemalägg ny uppdatering** och ange **Startdatum** till aktuell +1 minut.
1. Aktivera den schemalagda uppdateringen genom att köra kommandot `bin/magento cron:run --group=staging` i lokal miljö. Vänta i några minuter och kontrollera om schemat är aktivt.
1. Uppdatera sidan när schemat är aktivt.
1. Klicka **Visa/redigera** i avsnittet Schemalagda ändringar.
1. Redigera tiden genom att lägga till +2 minuter och spara ändringen.
1. Spara CMS-sidan.
1. Kör följande kommando igen: `bin/magento cron:run --group=staging`.
1. Klicka **Visa/redigera** av den schemalagda uppdateringen.

<u>Förväntade resultat</u>:

Användaren kan inte redigera starttiden för en aktiv schemalagd uppdatering.

<u>Faktiska resultat</u>:

Användaren får ett fel som *Det finns redan ett objekt (Magento\Cms\Model\Page) med samma ID &quot;11&quot;.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
