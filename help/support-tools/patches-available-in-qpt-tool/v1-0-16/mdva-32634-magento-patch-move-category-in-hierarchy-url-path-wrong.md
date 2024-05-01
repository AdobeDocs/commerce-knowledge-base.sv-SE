---
title: 'MDVA-32634-korrigering: flytta kategorin i hierarkiurl_path fel'
description: MDVA-32634-korrigeringen löser problemet där katalogkategorins url\_path inte ändras efter att kategorin har flyttats i hierarkin. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 är installerat. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.
exl-id: a445dea6-3834-479b-9044-b6d2b863a0b5
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# MDVA-32634-korrigering: flytta kategorin i hierarkiurl_path fel

MDVA-32634-korrigeringen löser problemet där katalogkategorins url\_path inte ändras efter att kategorin har flyttats i hierarkin. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 är installerat. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce om molninfrastruktur 2.3.4-p2

**Kompatibel med Adobe Commerce:**

Adobe Commerce om molninfrastruktur och Adobe Commerce lokalt 2.3.1 - 2.4.1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du flyttar en katalogkategori i hierarkin skapas en felaktig url\_path. URL:en\_path för den kategori som tilldelats standardarkivets omfång \[ **id:0** \] ändras inte när du har flyttat kategorin i hierarkin.

<u>Steg som ska återskapas</u>:

1. Logga in på Commerce Admin. Skapa följande kategoristruktur under rotkategorin: move-cat sub-move-cat sub-move-cat2 new-cat-move
1. Kontrollera attributet \[ url\_path \] \[ id: 120 \] för värdetilldelning i tabellen \[ catalog\_category\_entity\_varchar \] med hjälp av följande fråga:

   ```sql
   SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 4;
   ```

   Det ska ge följande resultat:

   ```sql
   MariaDB [m24dev]> SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 4;
   ```

   \[ url\_path \]-värden genererades och tilldelades till scopet \[ 0 \]. Det här är korrekt att jämföra med en instans utan B2B.
1. Gå till backend-kategorilistan, dra \[ move-cat \] och släpp den i \[ new-cat-move \]. Nu ska kategorin se ut så här: new-cat-move-cat sub-move-cat sub-move-cat2
1. Kontrollera tabellen \[ catalog\_category\_entity\_varchar \] med följande fråga:

   ```sql
   SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 16;
   ```

<u>Förväntade resultat</u>:

Den URL\_path som tilldelats alla butiksomfång \[ 0 \] bör också uppdateras med den nya sökvägen.

<u>Faktiska resultat</u>:

Den URL\_path som tilldelats alla butiksomfång \[ 0 \] ändras inte, även om det inte finns någon sådan sökväg efter flytten. Dessutom skapas nya url\_path-värden för varje butik.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
