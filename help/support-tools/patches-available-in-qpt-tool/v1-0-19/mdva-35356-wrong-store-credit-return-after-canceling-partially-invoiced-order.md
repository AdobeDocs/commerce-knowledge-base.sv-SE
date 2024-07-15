---
title: 'MDVA-35356: Fel butikskreditavkastning efter annullering av delvis fakturerad order'
description: MDVA-35356-korrigeringen åtgärdar problemet med felaktig butikskreditretur efter delvis fakturerad orderannullering. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Patch-ID:t är MDVA-35356. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.
exl-id: af37f318-0818-4393-b768-939f08b73847
feature: Invoices, Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# MDVA-35356: Fel butikskreditretur efter annullering av delvis fakturerad order

MDVA-35356-korrigeringen åtgärdar problemet med felaktig butikskreditretur efter delvis fakturerad orderannullering. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 är installerat. Patch-ID:t är MDVA-35356. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce i molninfrastruktur 2.4.1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.3.0-2.4.2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Skapa tre enkla produkter.
1. Skapa en ny användare och tilldela butikskredit (Exempel: butikskredit = *$10,* enkla produktpriser = *$100*, *$200* och *$300*).
1. Logga in med ovanstående användare och lägg de tre produkterna i kundvagnen.
1. Kolla in de tre produkterna i kundvagnen och använd butikskrediten för en del av ordern (Exempel: betalas med **check/Pengar-order**).
1. Utför två fakturor på beställningen via API:t, en för produkt 1 och en för produkt 2:

   ```php
   //endpoint POST {\{baseUrl}}/V1/order/:orderId/invoice    //1st API call:    {    "capture": true,    "items": [    {    "order_item_id": 1,    "qty": 1    }    ],    "notify": true,    "appendComment": false    }    //2nd API call:    {    "capture": true,    "items": [    {    "order_item_id": 2,    "qty": 1    }    ],    "notify": true,    "appendComment": false    }
   ```

1. Observera att butikskrediten tillämpas till fullo på den första fakturan.
1. &#x200B; Observera att butikens kreditsaldo = *0*.
1. Avbryt beställningen och se att två artiklar faktureras och att den tredje artikeln annulleras.
1. Observera butikens kreditsaldo.

<u>Förväntade resultat</u>:

Butikskreditsaldot är fortfarande 0 eftersom butikskrediten på 10 USD har fakturerats.

<u>Faktiska resultat</u>:

Hela butikskrediten returneras: saldot är 10 USD.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
