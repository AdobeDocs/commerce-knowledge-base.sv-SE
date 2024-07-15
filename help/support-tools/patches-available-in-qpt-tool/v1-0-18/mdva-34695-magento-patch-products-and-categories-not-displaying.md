---
title: "MDVA-34695: Produkter och kategorier visas inte"
description: MDVA-34695-korrigeringen löser problemet där produkter och kategorier inte visas i kategorirutnätet i Admin. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 är installerat. Korrigerings-ID är MDVA-34695. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.
exl-id: 0c2e50c1-648b-480a-a768-72af721950d8
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-34695: Produkter och kategorier visas inte

MDVA-34695-korrigeringen löser problemet där produkter och kategorier inte visas i kategorirutnätet i Admin. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 är installerat. Korrigerings-ID är MDVA-34695. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce i molninfrastruktur 2.3.4

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.0-2.4.0-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Negativa värden för `children_count` visas i databasen efter att kategorier har tagits bort.

<u>Steg som ska återskapas</u>:

1. Logga in på Admin Backend.
1. Navigera till **Katalog > Kategorier**.
1. Klicka på **Lägg till underkategori**.
1. Ange **kategorinamn** = *Överordnad 1* och spara sedan.
1. Klicka på **Lägg till underkategori**.
1. Ange **kategorinamn** = *Underordnat objekt 1* och spara sedan.
1. Klicka på **Lägg till underkategori**.
1. Ange **kategorinamn** = *Underordnad* och spara sedan.
1. Klicka på **Lägg till underkategori**.
1. Ange **kategorinamn** = *Underordnad 3* och spara sedan. Den här kategorin ska nu ha en nivå = *5*.
1. Klicka på kategorin **Underordnad 1**.
1. Ta bort kategorin.

<u>Förväntade resultat</u>:

Kategorirutnätet visar produkter och kategorier som förväntat.

<u>Faktiska resultat</u>:

Kategorirutnätet är tomt. Kontrollera tabellen `catalog_category_entity` i databasen. Observera att `children_count` blev negativ.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
