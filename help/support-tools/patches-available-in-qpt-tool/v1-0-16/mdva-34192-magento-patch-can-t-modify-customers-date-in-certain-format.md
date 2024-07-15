---
title: "MDVA-34192 patch: can't modify customers date in certain format"
description: MDVA-34192-korrigeringen åtgärdar ett problem där det är omöjligt att ändra/ange kundens födelsedatum i formatet dd/mm/åååå. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 är installerat. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.
exl-id: 8aa36970-b2bf-43f8-ba8f-bfc144f8d4ab
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-34192-korrigering: Det går inte att ändra kundens datum i vissa format

MDVA-34192-korrigeringen åtgärdar ett problem där det är omöjligt att ändra/ange kundens födelsedatum i formatet dd/mm/åååå. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 är installerat. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-version:** Adobe Commerce i molninfrastruktur 2.3.5-p1

**Kompatibel med Adobe Commerce-versioner:** 2.3.4-2.3.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Korrigeringen löser flera problem. Här följer en beskrivning och de steg som ska återges för en av dem.

Produktstödrasterfiltret fungerar inte korrekt när vi filtrerar med ett anpassat datumattribut och administratörens språkområde är en\_GB.

<u>Steg som ska återskapas:</u>:

1. Skapa en administratörsanvändare vars **Gränssnittsspråk** är inställt på *Engelska (Storbritannien)*.
1. Skapa ett datumattribut med följande konfiguration:
   * **Katalogindatatyp för butiksägare**: *Datum*
   * **Använd i filteralternativ**: *Ja*
   * **Lägg till i kolumnalternativ**: *Ja*
1. Tilldela attributet till en attributuppsättning.
1. Gå till produktredigeringssidan, välj ett datum för det nya attributet med datumväljaren och spara.
1. Försök att filtrera produktrutnätet med det nya datumattributet.

<u>Förväntat resultat:</u>:

Produktfiltret fungerar korrekt för ett anpassat datumattribut när administratörens nationella inställningar är en\_GB.

<u>Faktiskt resultat:</u>:

Produktfiltret fungerar inte korrekt för ett anpassat datumattribut när administratörens nationella inställningar är en\_GB.

## Tillämpa korrigeringen

Använd följande länkar, beroende på vilken Adobe Commerce-produkt du använder, för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT-verktyget finns i avsnittet [Patchar i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
