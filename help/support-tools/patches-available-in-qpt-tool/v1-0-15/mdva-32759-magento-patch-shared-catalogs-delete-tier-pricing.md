---
title: 'MDVA-32759-korrigering: delade kataloger raderar nivåpriser'
description: MDVA-32759-korrigeringen åtgärdar ett problem där delade kataloger tar bort befintliga nivåpriser.
exl-id: c6192d2f-cd25-483e-ba69-01ca62996faf
feature: B2B, Catalog Management
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# MDVA-32759-korrigering: delade kataloger raderar nivåpriser

MDVA-32759-korrigeringen åtgärdar ett problem där delade kataloger tar bort befintliga nivåpriser.

Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 är installerat. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce om molninfrastruktur 2.3.4-p2

**Kompatibel med Adobe Commerce:**

Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.0 - 2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Förutsättningar</u>:

Installera Adobe Commerce med B2B med **B2B-funktioner** aktiverat.

<u>Steg som ska återskapas</u>:

1. Gå till **Stores > Configuration > B2B Features > Enable Company** och **Delad katalog**.
1. Kör `bin/magento cron:run`.
1. Skapa en enkel produkt, klicka på **Avancerade priser** och lägga till **Katalog- och nivåpris** och sedan spara den.
1. Gå till **Katalog > Delad katalog > Ange priser och struktur**, klicka på **Konfigurera** och i den nedrullningsbara menyn avmarkerar du alla alternativ och sparar.
1. Kör `bin/magento cron:run`.
1. Öppna den produkt som skapats ovan och kontrollera de avancerade priserna.

<u>Förväntade resultat</u>:

Nivåpriserna bör inte tas bort från produkterna efter att alla produkter har tagits bort från den offentliga delade katalogen, som förväntat.

<u>Faktiska resultat</u>:

Nivåpriserna tas bort när alla produkter har tagits bort från den offentliga delade katalogen.


## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
