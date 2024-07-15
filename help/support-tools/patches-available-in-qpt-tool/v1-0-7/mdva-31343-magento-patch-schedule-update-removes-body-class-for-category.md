---
title: 'MDVA-31343-korrigering: schemauppdatering tar bort innehållsklass för kategori'
description: Korrigeringsfilen MDVA-31343 åtgärdar ett problem där CSS-klassen för den tilldelade layouten för en kategori tas bort under den schemalagda uppdateringen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat. Problemet är schemalagt att åtgärdas i Adobe Commerce 2.4.2.
exl-id: 50dbff01-cb77-4cac-b90e-5c4b06f5e4e7
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-31343-korrigering: schemauppdatering tar bort innehållsklass för kategori

Korrigeringsfilen MDVA-31343 åtgärdar ett problem där CSS-klassen för den tilldelade layouten för en kategori tas bort under den schemalagda uppdateringen. Den här korrigeringen är tillgänglig när [QPT-verktyget ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat. Problemet är schemalagt att åtgärdas i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce om molninfrastruktur 2.3.5-p2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Layoutbrödklassen tas bort från kategorin efter den schemalagda uppdateringen.

<u>Steg som ska återskapas</u>:

1. Skapa en kategori i Commerce Admin.
1. Ange **layout** = *Kategori - full bredd* i avsnittet **Design**.
1. Spara kategorin.
1. Gå till kategorisidan för frontend. I källdokumentet visas

   ```css
   page-layout-category-full-width
   ```

   CSS-klass.
1. Under **KATALOG** > **Kategori** klickar du på **Schemalägg ny uppdatering** i avsnittet *Schemalagda ändringar* för den nya kategorin.
1. Vänta på att den schemalagda uppdateringen ska starta, köra kron och tömma cachen.
1. Gå till kategorisidan på framsidan och kontrollera sidans källa.

<u>Förväntade resultat</u>:

I sidans brödtext visas

```css
page-layout-category-full-width
```

CSS-klass.

<u>Faktiska resultat</u>:

I sidans brödtext visas

```css
page-layout-2columns-left
```

CSS-klass, som är standard för kategorisidan.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som är tillgängliga i QPT finns i [korrigeringsfilerna i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
