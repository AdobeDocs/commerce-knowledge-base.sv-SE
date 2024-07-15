---
title: 'MDVA-37068: Felaktig moms visas vid utcheckning av virtuella produkter'
description: MDVA-37068-korrigeringen åtgärdar problemet när utcheckningssidan visar en felaktig skattesats för virtuella produkter. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 är installerat. Patch-ID:t är MDVA-37068. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: ef75b41e-e79d-4947-8b74-87966642f808
feature: Cache, Checkout, Orders, Products, Taxes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-37068: Felaktig moms visas vid utcheckning av virtuella produkter

MDVA-37068-korrigeringen åtgärdar problemet när utcheckningssidan visar en felaktig skattesats för virtuella produkter. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 är installerat. Patch-ID:t är MDVA-37068. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
Adobe Commerce om molninfrastruktur 2.3.5-p2

**Kompatibel med Adobe Commerce-versioner:**
Adobe Commerce (alla distributionsmetoder) 2.3.1-2.4.2-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Felaktig momssats visas på utcheckningssidan när kundvagnen bara har virtuella produkter.

<u>Förutsättningar</u>:

1. Skapa två separata skattesatser och skatteregler för två olika länder - till exempel 10 % och 1 %.
1. Skapa en virtuell produkt.
1. Kör omindexering och rensad cache.

<u>Steg som ska återskapas</u>:

1. Skapa en kund.
1. Lägg till olika fakturerings- och leveransadresser.
1. Lägg en virtuell produkt i kundvagnen.
1. Gå till sidan för kundvagn och utcheckning.

<u>Förväntade resultat</u>:

Momsen som visas på kundvagnen och kassasidan är densamma.

<u>Faktiska resultat</u>:

Momsen som visas på kundvagnen och kassasidan är INTE densamma.

## Tillämpa korrigeringen

Om du vill använda enskilda korrigeringsfiler använder du följande länkar beroende på distributionsmetod:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT-verktyget finns i avsnittet [Patchar i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
