---
title: 'MDVA-30977: produkter saknas i kategorier, indexering relaterat'
description: MDVA-30977-korrigeringen åtgärdar problem med produkter som visas på butikskategorisidor vid omindexering eller massåtgärder med ett stort antal produkter. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 är installerat. Problemen är planerade att åtgärdas i Adobe Commerce 2.4.2.
exl-id: 66ec4f53-c01d-4f87-a175-84f44a26f5d3
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# MDVA-30977: saknade produkter i kategorier, indexering relaterade

MDVA-30977-korrigeringen åtgärdar problem med produkter som visas på butikskategorisidor vid omindexering eller massåtgärder med ett stort antal produkter. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 är installerat. Problemen är planerade att åtgärdas i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

Korrigeringen skapades för Adobe Commerce i molninfrastruktur 2.3.4. Den är också kompatibel med Adobe Commerce lokalt 2.3.4.

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

### Utgåva 1

Antalet produkter som visas på kategorisidan i butiken skiljer sig åt efter att varje sida har lästs in igen under en masproduktuppdatering.

<u>Steg som ska återskapas:</u>

1. Skapa minst 30 000 produkter i två kategorier - minst 15 000 produkter i varje kategori.
1. Gå till **Katalog** > **Produkter** i handelsadministratören.
1. Välj alla produkter i rutnätet och utför en uppdatering av massattributet. Ange till exempel **Nytt** = *Ja* -attribut.
1. Kör Magento kron-jobbet med `bin/magento cron:run` kommandot två gånger.
1. Uppdatera kategorisidor på Storefront medan Adobe Commerce utför 30000 produktuppdateringar.

<u>Förväntat resultat:</u>

Antalet produkter i kategorier är alltid 15000 vid uppdatering av kategorisidor.

<u>Faktiskt resultat:</u>

Antalet produkter i kategorier är olika för varje kategorisiduppdatering.

### Utgåva 2

När hela omindexeringen av lagret utförs, blir kategorisidorna tomma och *Det går inte att hitta produkter som matchar markeringen* meddelandet visas.

<u>Steg som ska återskapas:</u>

1. Konfigurera Adobe Commerce med Elasticsearch.
1. Lägg till en ny webbplats.
1. Skapa en ny källa och tilldela den till den nya webbplatsen med Hantera lager.
1. Skapa 30000 konfigurerbara produkter.
1. Tilldela alla produkter till den nya webbplatsen och lägg även till lager till den nya lagerkällan.
1. Kör ett fullständigt omindexeringsintervall.
1. Kör omindexering av lager genom att köra `bin/magento indexer:reindex inventory`
1. Bläddra i en kategori med många produkter.

<u>Förväntat resultat:</u>

Kategorisidor visar produkter som vanligt vid omindexering.

<u>Faktiskt resultat:</u>

Kategorisidor blir tomma under omindexering.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) -avsnitt.
