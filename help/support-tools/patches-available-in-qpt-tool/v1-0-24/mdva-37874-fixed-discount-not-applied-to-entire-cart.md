---
title: 'MDVA-37874: Fast rabatt gäller inte för hela kundvagnen'
description: MDVA-37874-korrigeringen åtgärdar problemet när **fast rabattbelopp** för hela kundvagnen felaktigt tillämpas på en paketprodukt som innehåller mer än ett alternativ. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.24 är installerat. Patch-ID:t är MDVA-37874. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.
exl-id: a1c414f0-b654-4b18-b502-47351513ddfa
feature: Orders, Personalization, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# MDVA-37874: Fast rabatt gäller inte för hela kundvagnen

MDVA-37874-korrigeringen åtgärdar problemet när **fast rabattbelopp** för hela varukorgen appliceras felaktigt på en paketprodukt som innehåller mer än ett alternativ. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.24 är installerat. Patch-ID:t är MDVA-37874. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

* Korrigeringen har utformats för Adobe Commerce i molninfrastruktur 2.4.2
* Korrigeringen är även kompatibel med Adobe Commerce lokalt och Adobe Commerce i molninfrastrukturen 2.3.6-2.3.7 och 2.4.1-2.4.2-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem


<u>Steg som ska återskapas</u>:

1. Skapa en kundvagnsregel med en **fast rabattbelopp** för hela vagnen.
1. Lägg en paketprodukt i kundvagnen (paketprodukten ska innehålla flera valda alternativ.)
1. Gå till kundvagnssidan och kontrollera rabatten.


<u>Förväntade resultat</u>:

Det fasta rabattbeloppet används som förväntat på hela kundvagnen.

<u>Faktiska resultat</u>:

Det fasta rabattbeloppet gäller endast en del av kundvagnen.


## Tillämpa korrigeringen

Använd följande länkar, beroende på vilken Adobe Commerce-produkt du använder, för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som finns i QPT-verktyget finns i [Patchar tillgängliga i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
