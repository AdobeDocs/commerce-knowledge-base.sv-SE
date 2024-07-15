---
title: 'MDVA-37224: Det går inte att betala "överlåtbar offert" med PayFlow Pro'
description: MDVA-37224-korrigeringen åtgärdar problemet när kunderna inte kan betala för en **Negotiable Quote** med Paypal PayFlow Pro. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 är installerat. Korrigerings-ID är MDVA-37224. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.
exl-id: df75b38d-64c8-46b5-85ff-7606ce1dfd34
feature: B2B, Orders, Payments, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-37224: Det går inte att betala &quot;överlåtbar offert&quot; med PayFlow Pro

MDVA-37224-korrigeringen åtgärdar problemet när kunderna inte kan betala för en **Negotiable Quote** med Paypal PayFlow Pro. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 är installerat. Korrigerings-ID är MDVA-37224. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

* Korrigeringen har utformats för Adobe Commerce i molninfrastrukturen 2.3.6-p1
* Korrigeringen är även kompatibel med Adobe Commerce lokalt och Adobe Commerce i molninfrastrukturen 2.3.3-2.4.2-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Förutsättningar</u>:

* Adobe Commerce med en installerad B2B-modul
* Företagsfunktionalitet aktiverad
* Funktionen **Förhandlingsbar offert** har aktiverats
* En företagsanvändare finns
* Betalningsmetoden PayPal PayFlow Pro är aktiverad och konfigurerad
* Betalningsmetoden PayPal PayFlow Pro är tillåten för B2B
* 2 produkter med olika priser har skapats

<u>Steg som ska återskapas</u>:

1. Öppna Storefront.
1. Lägg **Produkt 1** i kundvagnen.
1. Skapa en **förhandlingsbar offert** för **Produkt 1**.
1. Lägg **Produkt 2** i kundvagnen.
1. Acceptera den **förhandlbara offerten** som skapats i steg 3 från Admin.
1. Öppna den här **förhandlingsbara offerten** från Storefront och fortsätt till kassan.
1. Välj **Betalningsmetod** = *PayPal PayFlow Pro* i steget **Granska och betala**.
1. Beställ.

<u>Förväntade resultat</u>:

* Ordern har placerats som förväntat.
* PayPal skickar e-post med rätt information till kunden som förväntat.

<u>Faktiska resultat</u>:

* Webbsidan hänger och slutför inte ordern.
* PayPal skickar en bekräftelse till kunden med nollvärden som liknar det här exemplet:

```php
Order ID: A1xxxxxxxxx
Order Placed: Monday, April 21, 2021 01:12:12 PM PDT

Shipping Amount: $0.00
Tax Amount: $0.00
Amount of Transaction: $0.00
Payment Type: Visa

BILL TO
--------
US
```


## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* 
   * [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
