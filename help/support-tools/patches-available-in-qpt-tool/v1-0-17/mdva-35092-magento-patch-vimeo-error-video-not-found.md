---
title: 'MDVA-35092: Vimeo-fel: "Video not found"'
description: 'Korrigeringen MDVA-35092 åtgärdar ett fel där följande fel visas: *"Video hittades inte"*. Det här felmeddelandet visas när du anger en Vimeo-video med det inbyggda Lägg till video-gränssnittet i produktadministratören för Adobe Commerce. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3."'
exl-id: bc0952d9-1ea4-417c-926c-96875984d82c
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# MDVA-35092: Vimeo-fel: &quot;Video not found&quot;

MDVA-35092-korrigeringen åtgärdar ett problem där felmeddelandet visas: *&quot;Video hittades inte&quot;*. Det här felmeddelandet visas när du anger en Vimeo-video med det inbyggda Lägg till video-gränssnittet i produktadministratören för Adobe Commerce. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce i molninfrastruktur 2.4.1

**Kompatibel med Adobe Commerce:**

Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.5 - 2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Vimeos enkla API slutar fungera som förväntat.

<u>Steg som ska återskapas</u>:

1. Logga in på Admin.
1. Gå till om du vill redigera en befintlig produkt **KATALOG** > **Produkter** > **Redigera** eller om du vill skapa en ny produkt går du till **KATALOG** > **Produkter** > **Redigera** > **Lägg till produkt**.
1. Klicka på **Bilder och video** på produktsidan.
1. Klicka **Lägg till video** och lägga till en Vimeo-videos URL. Klicka **Spara**.

<u>Förväntade resultat</u>:

Den nya videon hittas och sparas.

<u>Faktiska resultat</u>:

Fel: *&quot;Video hittades inte&quot;* visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
