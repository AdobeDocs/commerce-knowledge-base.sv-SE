---
title: "MDVA-34680: Kundkontot har inte filtrerats korrekt i kundens rutnät"
description: MDVA-34680-korrigeringen åtgärdar problemet när kundkontot som skapats efter 00:00 UTC inte filtreras korrekt i kundens rutnät. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 är installerat. Korrigerings-ID är MDVA-34680. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.
exl-id: 2e506d7a-8cde-41eb-84b2-1a5ff8015428
feature: Customer Service
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-34680: Kundkontot har inte filtrerats korrekt i kundens rutnät

MDVA-34680-korrigeringen åtgärdar problemet när kundkontot som skapats efter 00:00 UTC inte filtreras korrekt i kundens rutnät. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 är installerat. Korrigerings-ID är MDVA-34680. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce i molninfrastruktur 2.4.1 och 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.6-2.3.7 och 2.4.1-2.4.2-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När ett kundkonto har skapats efter 00:00 UTC och du försöker filtrera konton vid det datumet returneras inte den här kunden.

<u>Steg som ska återskapas</u>:

1. Gå till **Lagrar** > **Konfiguration** > **Allmänt** och ange tidszonen som Eastern Standard [United States/New York].
1. Skapa ett nytt kundkonto efter 00:00 UTC.
1. Gå till **Kunder** > **Alla kunder** och filtrera konton efter dagens datum.

<u>Förväntade resultat</u>:

Kundkontofiltren visar det nya kontot som skapats idag efter 00:00 UTC.

<u>Faktiska resultat</u>:

Kundkontofiltren visar inte det nya konto som skapats idag.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
