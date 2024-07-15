---
title: "MDVA-37082: Felaktigt partiellt index för lagerstatus för grupperade produkter"
description: Patchen MDVA-37082 Magento åtgärdar problemet när partiellt index för lagerstatus för grupperade produkter är fel för anpassade lager. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 är installerat. Patch-ID:t är MDVA-37082. Observera att problemet är planerat att åtgärdas i Magento 2.4.4.
exl-id: 1c0abc99-bd24-4848-87a3-227a63655cb7
feature: Cache, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# MDVA-37082: Felaktigt partiellt index för lagerstatus för grupperade produkter

Patchen MDVA-37082 Magento åtgärdar problemet när partiellt index för lagerstatus för grupperade produkter är fel för anpassade lager. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 är installerat. Patch-ID:t är MDVA-37082. Observera att problemet är planerat att åtgärdas i Magento 2.4.4.


## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
Adobe Commerce om molninfrastruktur 2.3.4-p2

**Kompatibel med Adobe Commerce-versioner:**
Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.0-2.4.2-p1
>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Inkrementell indexering av underordnade grupperade produkter kan leda till att felaktiga andra grupperade produkter indexeras felaktigt när underordnade objekt delas.

<u>Steg som ska återskapas</u>:

* Skapa ett nytt arkiv och en ny källa för huvudwebbplatsen.
* Skapa tre enkla produkter med kvantiteten 10,15 och 0.
* Skapa två grupperade produkter och tilldela en första enkel produkt med kvantitet 10 till en och två andra enkla produkter till den andra.
* Bekräfta att båda grupperade produkter kan nås från frontend, i lager.
* Tilldela den enkla produkten med kvantitet 0 till den första grupperade produktens Up-Sell-produkter.
* Rensa helsidescachen och kontrollera den andra grupperade produkten från förgrunden.
* Kör ett fullständigt omindex.
* Kontrollera den andra grupperade produkten från frontend.
* Spara den första grupperade produkten.
* Rensa helsidescachen och kontrollera den andra grupperade produkten från förgrunden.

<u>Förväntade resultat</u>:

Grupperad produkt finns inte i lager när en annan grupperad produkt har sparats med merförsäljning. Problemet åtgärdas efter en fullständig indexering.

<u>Faktiska resultat</u>:

Den andra grupperade produkten går ur lager när du sparar den första grupperade produkten.

## Tillämpa korrigeringen

Om du vill tillämpa enskilda korrigeringsfiler använder du följande länkar till utvecklardokumentationen, beroende på vilken distributionsmetod du använder i Adobe Commerce:

* Lokalt hos Adobe Commerce: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Kontrollera om det finns en korrigeringsfil för ditt Magento-problem med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Mer information om andra tillgängliga korrigeringsfiler i QPT-verktyget finns i avsnittet [Patchar i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
