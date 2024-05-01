---
title: MDVA-28357 SKU-sökning på sidan Avancerad sökning fungerar inte
description: MDVA-28357 löser problemet där sökning på en produkt-SKU på sidan Avancerad sökning inte leder till att den relevanta produkten visas i sökresultaten. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8 är installerat. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.1.
exl-id: a89409b0-3155-4fac-9842-0d129dacd6e1
feature: Search
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-28357 SKU-sökning på sidan Avancerad sökning fungerar inte

MDVA-28357 löser problemet där sökning på en produkt-SKU på sidan Avancerad sökning inte leder till att den relevanta produkten visas i sökresultaten. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8 är installerat. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.1.

## Berörda produkter och versioner

* Den här korrigeringen är avsedd för Adobe Commerce lokalt 2.3.4-p2.
* Korrigeringen är även kompatibel med Adobe Commerce lokalt och Adobe Commerce i molninfrastrukturen 2.3.0 till 2.3.5-p2 och 2.4.0 till 2.4.0-p1.

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Vid avancerad sökning används jokertecken för att söka med hjälp av en SKU-enhet för att söka i SKU-fältet. Men ett jokertecken kan bara användas med `sku.keyword`så detta returnerar inte den förväntade produkten.

<u>Steg som ska återskapas</u>

1. Gå till sidan Avancerad sökning.
1. Sök på SKU-nummer.

<u>Faktiskt resultat</u>

Felmeddelandet visas: *Det går inte att hitta några objekt som matchar sökvillkoren. Ändra sökningen*.

<u>Förväntat resultat</u>

En produktartikel visas med ett meddelande: *1 objekt hittades med följande sökvillkor*  *SKU: XX-XXXX*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Tillämpa korrigeringar med verktyget Korrigera kvalitet](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Mer information om andra korrigeringsfiler som finns i QPT-verktyget finns i [Patchar tillgängliga i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
