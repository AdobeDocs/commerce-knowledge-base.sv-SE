---
title: 'MDVA-34886: inga sökresultat när attributet "weight" används'
description: MDVA-34886-korrigeringen löser problemet där sökningen returnerar resultat när viktattributet är konfigurerat som sökbart. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 är installerat. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.
exl-id: e6f33772-0167-4a54-9d62-0ab89edb5d1d
feature: Attributes, Cache, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-34886: inga sökresultat när attributet Weight används

MDVA-34886-korrigeringen löser problemet där sökningen returnerar resultat när viktattributet är konfigurerat som sökbart. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 är installerat. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce om molninfrastruktur 2.3.5-p1

**Kompatibel med Adobe Commerce:**

Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.2 - 2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Sökningen returnerar resultat när viktattributet är konfigurerat som sökbart.

<u>Steg som ska återskapas</u>:

1. Konfigurera Elasticsearch.
1. Navigera till **Administratör** > **Lager** > **Attribut** > **Produkt**. Redigera **Bredd** och ange dess attribut **Sökbart** = *Ja*.
1. Spara attributet och rensa konfigurationscachen.
1. Sök efter ett textvärde (Exempel: *bag*).
1. Observera att sökningen inte returnerar några resultat.
1. Undantagsloggen innehåller ett felmeddelande som:

```php
{"type":"number_format_exception","reason":"For input string: \"bag\""}
```

<u>Förväntade resultat</u>:

Sökningen returnerar resultat även när viktattributet är konfigurerat som sökbart, som förväntat.

<u>Faktiska resultat</u>:

Sökningen returnerar inga resultat när viktattributet är konfigurerat som sökbart.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
