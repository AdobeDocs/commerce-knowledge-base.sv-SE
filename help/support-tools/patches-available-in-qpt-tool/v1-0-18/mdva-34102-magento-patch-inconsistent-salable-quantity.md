---
title: 'MDVA-34102: inkonsekvent säljbar kvantitet'
description: MDVA-34102-korrigeringen åtgärdar ett problem där standardlagret är noll för inaktiverade produkter i produktstödrastret och Redigera produktsidor i Admin. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 är installerat. Korrigerings-ID är MDVA-34102. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.
exl-id: cb1d4689-c122-4afd-8597-b2627027aaf3
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-34102: Inkonsekvent säljbar kvantitet

MDVA-34102-korrigeringen åtgärdar ett problem där standardlagret är noll för inaktiverade produkter i produktstödrastret och Redigera produktsidor i Admin. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 är installerat. Korrigerings-ID är MDVA-34102. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce om molninfrastruktur 2.3.5-p2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.3.0-2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Konfigurera två webbplatser med butiker och butiksvyer.
1. Skapa ytterligare en källa och ett lager.
1. Lägg till en enkel produkt:
   * Ange **Aktivera produkt** = *Nej*.
   * Tilldela två källor med **Source objektstatus** = *I Stock* med en kvantitet som är större än noll (Exempel: **standardlager** = *123* och **brittiskt lager** = *123*).
1. Spara produkten.
1. Kontrollera fliken **Produkt, säljbart antal**.

<u>Förväntade resultat</u>:

Både standardstammen och den brittiska stammen = *123.*

Antalet standardlager visas korrekt för inaktiverade produkter på sidorna för produktstödraster och Redigera produkt i administratören.

<u>Faktiska resultat</u>:

Standardaktie = *0* och brittisk aktie = *123.*

Antalet standardlager är noll för inaktiverade produkter i produktstödrastret och Redigera produktsidor i administratören.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT-verktyget finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
