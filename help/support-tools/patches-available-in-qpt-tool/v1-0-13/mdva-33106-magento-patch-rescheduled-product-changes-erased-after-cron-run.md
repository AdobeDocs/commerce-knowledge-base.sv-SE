---
title: "MDVA-33106-korrigering: Omschemalagda produktändringar som raderats efter kron körning"
description: MDVA-33106-korrigeringen åtgärdar ett problem där de omlagda produktändringarna raderas efter kronen
exl-id: be32982c-796c-4069-ad70-37b5124ffb56
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-33106-korrigering: Omschemalagda produktändringar raderas efter kronkörning

MDVA-33106-korrigeringen åtgärdar ett problem där de omlagda produktändringarna raderas efter kronen

```bash
bin/magento cron:run
```

kommandot körs. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 är installerat. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce om molninfrastruktur 2.3.5-p2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.0 - 2.4.1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Gå till **Katalog** > **Produkter** i Commerce Admin och klicka på Redigera. Observera värdet **Price**, till exempel *9.99*.
1. Klicka på **Schemalägg ny uppdatering** och fyll i detaljer:
   * Uppdateringsnamnet är inte viktigt.
   * Ange ett datum i framtiden, +1 år för startdatum och slutdatum.
   * Ange priset till *1,99*.
   * Spara ändringar.
1. Gå till kontrollpanelen för innehållstagning och välj stödrastervyn för att se om det finns någon schemalagd matchning ovan.
1. Välj redigeringsåtgärd bredvid den schemalagda uppdateringen. Data ska fortfarande överensstämma ovan.
1. Ändra schemalagt datum till något närmare. Byt till 1 vecka eller + 1 månad i stället för +1 år från och med nu.
1. Spara ändringar och kontrollera om datumen har uppdaterats på mellanlagringspanelen.
1. Vänta på att ett cron-jobb körs.
1. Klicka på Redigera igen i den schemalagda ändringen och kontrollera priset.

<u>Förväntade resultat</u>:

Priset är 1,99.

<u>Faktiska resultat</u>:

Priset är 9,99.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som är tillgängliga i QPT finns i [korrigeringsfilerna i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
