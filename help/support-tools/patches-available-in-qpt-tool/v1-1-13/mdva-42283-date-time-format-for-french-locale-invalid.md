---
title: 'MDVA-42283: Formatet Date-time för franska är ogiltigt'
description: Korrigeringen MDVA-42283 åtgärdar ett problem där datumet-time-formatet i administrationsorderrutnätet för franska är ogiltigt. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 är installerat. Korrigerings-ID är MDVA-42283. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 9b470e7b-4b73-4100-9a9d-1a45a5ac628b
feature: CMS
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-42283: Formatet Date-time för franska är ogiltigt

Korrigeringen MDVA-42283 åtgärdar ett problem där datumet-time-formatet i administrationsorderrutnätet för franska är ogiltigt. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 är installerat. Korrigerings-ID är MDVA-42283. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Formatet för datum/tid i administrationsorderrutnätet för franska är ogiltigt.

<u>Steg som ska återskapas</u>:

1. Skapa en beställning, kund, CMS-sida eller CMS-block.
1. Gå till **Administratör** > **Kontoinställningar** och ange gränssnittets språkområde för administratören **Français (Kanada)**/**français (Kanada)(fr_CA)** eller **Brasiliansk portugisiska (pt_BR)**.
1. Observera värdet i datumkolumnen för rutnät för beställningar, leveranser, kreditnotor, kunder, CMS-sidor eller CMS-block.

<u>Förväntade resultat</u>:

Datumet har det format som visas på den faktiska redigeringssidan för entiteten.

<u>Faktiska resultat</u>:

Datum-tid-värdet är felaktigt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
