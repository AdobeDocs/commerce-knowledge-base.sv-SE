---
title: 'MDVA-36853: Inga bilder läses in från stora mediegallerier'
description: Korrigeringen MDVA-36853 åtgärdar problemet när inga bilder läses in eftersom widgeten för sidbyggarmediegalleri inte läses in när du har en stor mediekatalog.
exl-id: 64e089d9-d443-4aa7-8e04-a3598b05958d
feature: CMS, Cache, Media
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# MDVA-36853: Inga bilder läses in från stora mediegallerier

Korrigeringen MDVA-36853 åtgärdar problemet när inga bilder läses in eftersom widgeten för sidbyggarmediegalleri inte läses in när du har en stor mediekatalog.

Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 är installerat. Patch-ID:t är MDVA-36853. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:** Adobe Commerce i molninfrastruktur 2.4.2

**Kompatibel med Adobe Commerce:** Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Ange **Aktivera gammalt mediegalleri** = *Ja* in **Admin > Stores > Configuration > Advanced > System > Media gallery**.
1. Navigera till **Innehåll > Block** och skapa ett nytt CMS-block eller redigera ett befintligt CMS-block.
1. Klicka på **Redigera med PageBuilder** -knappen.
1. Lägg till ett mediaelement.
1. Klicka på **Välj från galleri** -knappen.

<u>Förväntade resultat</u>:

Widgeten för mediegalleriet och mediegalleribilderna läses in som förväntat.

<u>Faktiska resultat</u>:

Både mediegalleriwidgeten och mediegalleribilderna läses inte in när du har en stor `pub/media/catalog/product/cache/` katalog.

## Tillämpa korrigeringen

Använd följande länkar, beroende på vilken Adobe Commerce-produkt du använder, för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som finns i QPT-verktyget finns i [Patchar tillgängliga i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
