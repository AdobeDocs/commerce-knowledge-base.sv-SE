---
title: 'MDVA-38468: Ta emot ett felmeddelande när CMS-sidan sparas'
description: '"Korrigeringen MDVA-38468 Adobe Commerce åtgärdar ett problem där felmeddelandet visas: *Objekt med samma ID "PAGE_ID" finns redan* när en CMS-sida sparas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.26 är installerat. Patch-ID:t är MDVA-38468. Observera att problemet har åtgärdats i Adobe Commerce 2.3.6."'
exl-id: 7fe80308-50b7-4786-a43c-cce607eb606c
feature: CMS, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-38468: Ta emot ett felmeddelande när CMS-sidan sparas

MDVA-38468 Adobe Commerce-korrigeringen åtgärdar ett problem där användare får felmeddelandet: *Objekt med samma ID,&quot;PAGE_ID&quot;,* när en CMS-sida sparas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.26 är installerat. Patch-ID:t är MDVA-38468. Observera att problemet har åtgärdats i Adobe Commerce 2.3.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
Adobe Commerce om molninfrastruktur 2.3.2-p2

**Kompatibel med Adobe Commerce-versioner:**
Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.2-2.3.5-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du försöker spara en CMS-sida får du följande felmeddelande: *Det finns redan ett objekt med samma ID &quot;PAGE_ID&quot;.*

<u>Steg som ska återskapas</u>:

1. Skapa en ny webbplats + Store + Store + Store.
1. Skapa en webbplats till + Store + Store + Store.
1. Gå till **Innehåll** > **Hierarki** > Lägg till en befintlig CMS-sida i hierarkiträdet.
1. Gå till **Innehåll** > **Sidor** > **Lägg till ny sida**:
   * Lägg till en titel.
   * I avsnittet Sida på webbplatser tilldelar du till båda skapade Stock-granskningar.
   * I avsnittet Hierarki tilldelar du valfri kategori.
   * **Spara och fortsätt redigera**.

<u>Förväntade resultat</u>:

Sidan sparas utan fel.

<u>Faktiska resultat</u>:

Sidan sparas, men följande felmeddelande visas: *Objektet (Magento\VersionsCms\Model\Hierarchy\Node) med samma ID &quot;PAGE_ID&quot; finns redan.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT-verktyget finns i avsnittet [Patchar i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
