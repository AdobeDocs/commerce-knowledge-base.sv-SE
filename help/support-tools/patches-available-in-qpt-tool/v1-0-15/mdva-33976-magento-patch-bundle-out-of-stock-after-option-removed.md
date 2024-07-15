---
title: 'MDVA-33976 patch: bundle Out Of Stock after option removed'
description: MDVA-33976-korrigeringen åtgärdar ett problem där en paketprodukt visas som"Out Of Stock" efter att ett av dess alternativ har tagits bort i Admin. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool) 1.0.15](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) är installerat. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.
exl-id: 2e2bc05b-ad31-4e87-b33e-3526f6a42478
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-33976-korrigering: Paketet tas bort från Stock efter att alternativet tagits bort

MDVA-33976-korrigeringen åtgärdar ett problem där en paketprodukt visas som&quot;Out Of Stock&quot; efter att ett av dess alternativ har tagits bort i Admin. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool) 1.0.15](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) är installerat. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-version:** Adobe Commerce i molninfrastruktur 2.3.3

**Kompatibel med Adobe Commerce-versioner:** Adobe Commerce i molninfrastruktur och Adobe Commerce lokalt 2.3.0-2.3.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Öppna en paketprodukt i Commerce Admin.
1. Ta bort ett av produktalternativen.
1. Spara ändringar.
1. Öppna produkten i butiken.

<u>Förväntat resultat</u>:

Paketets produktlagerstatus uppdateras enligt statusen för den underordnade produkten.

<u>Faktiskt resultat</u>:

Paketprodukten visas som Ej i lager, oavsett status för den underordnade produkten.

## Tillämpa korrigeringen

Använd följande länkar, beroende på vilken Adobe Commerce-produkt du använder, för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT-verktyget finns i avsnittet [Patchar i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
