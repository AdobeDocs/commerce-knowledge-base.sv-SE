---
title: 'MDVA-41164: Det går inte att spara eller redigera företag med anpassade kundattribut'
description: MDVA-41164-korrigeringen löser problemet där administratörsanvändaren inte kan spara eller redigera ett företag med anpassade kundattribut för filer eller bilder av någon typ. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 är installerat. Korrigerings-ID är MDVA-41164. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: 24338895-68b4-404c-bedd-46cfc7e983a0
feature: Admin Workspace, Attributes, B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-41164: Det går inte att spara eller redigera företag med anpassade kundattribut

MDVA-41164-korrigeringen löser problemet där administratörsanvändaren inte kan spara eller redigera ett företag med anpassade kundattribut för filer eller bilder av någon typ. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 är installerat. Korrigerings-ID är MDVA-41164. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörsanvändaren kan inte spara eller redigera ett företag med anpassade kundattribut för filer eller bilder av någon typ.

<u>Förutsättningar</u>:

B2B-modulen är installerad.

<u>Steg som ska återskapas</u>:

1. Aktivera företag i **Lager** > **Konfig** > **B2B-funktioner**.
1. Skapa ett kundattribut i **Lager** > **Attribut** > **Kunder** > **Lägg till nytt attribut**:
   * Indatatyp: Fil (bifogad)
   * Visa på Storefront: Ja
   * Sorteringsordning: Alla
   * Forms att använda i: Markera alla
1. Skapa ett nytt företag i **Kunder** > **Företag** > **Lägg till nytt företag** och överför en fil för det nya attributet som skapas ovan.

<u>Förväntade resultat</u>:

Användaren kan slutföra skapandet av företaget och bilagan överförs utan fel.

<u>Faktiska resultat</u>:

* Du får ett felmeddelande: *Något gick fel när filen sparades.*
* Undantagsloggen innehåller en post som följande:

  ```php
  report.CRITICAL: Notice: Undefined index: customer in
  ../app/code/Magento/Customer/Controller/Adminhtml/File/Customer/Upload.php on line 69
  ```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) -avsnitt.
