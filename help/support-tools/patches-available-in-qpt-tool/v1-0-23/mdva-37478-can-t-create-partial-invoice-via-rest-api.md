---
title: "MDVA-37478: Det går inte att skapa en del av en faktura via REST API"
description: Korrigeringen MDVA-37478 åtgärdar problemet när du inte kan skapa en partiell faktura via REST API för en beställning som gjorts med betalningsmetod **Betalning på konto**. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 är installerat. Patch-ID:t är MDVA-37478. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.
exl-id: 1b235baa-a188-467c-8ae5-de0836bc2caa
feature: REST, B2B, Invoices
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-37478: Det går inte att skapa partiell faktura via REST API

Korrigeringen MDVA-37478 åtgärdar problemet när du inte kan skapa en partiell faktura via REST API för en beställning som gjorts med betalningsmetod **Betalning à conto**. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 är installerat. Patch-ID:t är MDVA-37478. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

* Korrigeringen har utformats för Adobe Commerce i molninfrastrukturen 2.3.3-p1
* Korrigeringen är även kompatibel med Adobe Commerce lokalt och Adobe Commerce i molninfrastrukturen 2.3.0-2.3.7

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Förutsättning</u>:

Adobe Commerce med en installerad B2B-modul

<u>Steg som ska återskapas</u>:

1. Aktivera **B2B-företag**.
1. Aktivera **Betalning à conto** betalningsmetod.
1. Skapa två enkla produkter.
1. Skapa ett företag.
1. Lägg till företagskrediter som överstiger det totala priset för två skapade produkter.
1. Logga in på klientsidan med det företagskonto som skapats.
1. Lägg de två produkter som skapats i kundvagnen och beställ med **Betalning à conto** betalningsmetod.
1. Försök att skapa en delfaktura för den order som skapats via REST API:

   ```php
   POST /rest/V1/order//invoice
   {
     "items": [
       {
         "order_item_id": 2,
         "qty": 1
       }
     ]
   }
   ```

<u>Förväntade resultat</u>:

Den partiella fakturan skapas för en order som gjorts med **Betalning à conto** betalningsmetod, som förväntat.

<u>Faktiska resultat</u>:

Följande fel returneras från REST API:

```php
{"message":"Invoice Document Validation Error(s):\nAn invoice for partial quantities cannot be issued for this order. To continue, change the specified quantity to the full quantity."}
```

## Tillämpa korrigeringen

Använd följande länkar, beroende på vilken Adobe Commerce-produkt du använder, för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra korrigeringsfiler som finns i QPT-verktyget finns i [Patchar tillgängliga i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
