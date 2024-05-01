---
title: 'MDVA-34012 patch: attributkryssrutan har ändrats i fel'
description: MDVA-34012-korrigeringen löser problemet där kryssrutan för ett attribut ändras efter en schemauppdatering av misstag.
exl-id: 1a8f1bea-9b6a-4984-b9f0-b2b9ceb6688f
feature: Attributes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# MDVA-34012-korrigering: attributkryssrutan har ändrats

MDVA-34012-korrigeringen löser problemet där kryssrutan för ett attribut ändras efter en schemauppdatering av misstag.

Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.17 är installerat. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:** Adobe Commerce om molninfrastruktur 2.3.5-p2

**Kompatibel med Adobe Commerce:** Adobe Commerce om molninfrastruktur och Adobe Commerce lokalt 2.3.1 - 2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Logga in på Admin och navigera till **Katalog > Produkter**.
1. Redigera alla enkla produkter.
1. Ändra butiksvyn till en viss butiksvy.
1. Spara produkten med **Använd standardvärde** markerad kryssruta för ett attribut (Exempel: **Aktivera produkt** attribut).
1. Klicka på **Schemalägg ny uppdatering** för att schemalägga vissa ändringar (Exempel: **Pris** eller **Specialpris** för en viss butiksvy).
1. Vänta tills ändringarna är klara.
1. Kontrollera produkten. Den bör ha sin kryssruta avmarkerad och ha ett specifikt butiksattributvärde.

<u>Förväntade resultat</u>:

Kryssrutan för attributet ska vara densamma och ändras inte som förväntat efter schemauppdateringen.

<u>Faktiska resultat</u>:

Kryssrutan för attributet ändras efter schemauppdateringen.

## Tillämpa korrigeringen

Använd följande länkar, beroende på vilken Adobe Commerce-produkt du använder, för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som finns i QPT-verktyget finns i [Patchar tillgängliga i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
