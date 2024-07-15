---
title: "MDVA-23764 Magento patch: error when loading dynamic blocks"
description: Korrigeringen MDVA-23764 Magento åtgärdar felet i
exl-id: b884ade6-f88d-4c79-8e84-5a59252abb75
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# MDVA-23764 Magento patch: fel vid inläsning av dynamiska block

Korrigeringen MDVA-23764 Magento åtgärdar felet i

```php
JsFooterPlugin.php
```

som påverkar visningen av dynamiska block. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 är installerat. Observera att problemet löstes i Magento 2.3.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Magento-version:** Magento Commerce Cloud 2.3.3.

**Kompatibel med Magento-versioner:** Magento Commerce och Magento Commerce Cloud 2.3.2 - 2.3.4-p2.

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg att återskapa:</u>

Försök att läsa in en URL som ser ut så här: https://\[magento domain\]/banner/ajax/load/.

<u>Faktiskt resultat:</u>

Ett fel som liknar följande inträffar: *Uncaught TypeError: strpos() förväntar att parameter 1 ska vara sträng, null anges i..(kodrad)* .

<u>Förväntat resultat:</u>

URL-adressen läses in utan fel.

## Tillämpa korrigeringen

Instruktioner om hur du använder en QPT-korrigering finns på följande länkar beroende på din Magento-produkt:

* Magento Commerce: DevDocs [Tillämpa korrigeringar med verktyget för kvalitetspatchar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) .
* Magento Commerce Cloud: DevDocs [Upgrades and Patches > Apply patches](https://devdocs.magento.com/cloud/project/project-patch.html) .

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget Kvalitetspatchar släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [Kontrollera om det finns en korrigeringsfil för ditt Magento-problem med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

Mer information om andra tillgängliga korrigeringsfiler i QPT-verktyget finns i avsnittet [Patchar i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
