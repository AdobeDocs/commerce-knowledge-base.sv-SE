---
title: 'MDVA-38270: Presentkortsbelopp saknas i kundordersumman'
description: MDVA-38270-korrigeringen åtgärdar problemet när presentkortsbeloppet inte hittas i kundordersumman. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 är installerat. Patch-ID:t är MDVA-38270. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.
exl-id: 4ab315c4-d26e-4270-a556-66601d01fb2e
feature: Gift, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# MDVA-38270: Presentkortsbelopp saknas i Kundordersumma

MDVA-38270-korrigeringen åtgärdar problemet när presentkortsbeloppet inte hittas i kundordersumman. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 är installerat. Patch-ID:t är MDVA-38270. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**
Adobe Commerce om molninfrastruktur 2.4.2-p1

**Kompatibel med Adobe Commerce:**
Adobe Commerce (alla distributionsmetoder) 2.4.1-2.4.2-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Presentkortsbelopp saknas i orderns totala svar.

<u>Förutsättningar</u>:

1. Skapa ett kundkonto.
1. Beställ med ett presentkort (presentkortet täcker hela beställningen).

<u>Steg som ska återskapas</u>:

Gör en kundfråga för kund, order, artiklar, totalt:

```GraphQL
query {
  customer {
    orders(
      pageSize: 20
    ) {
      items {
        id
        order_date
        total {
          grand_total {
            value
            currency
          }
          total_giftcard {
              applied_balance {
                value
                currency
              }
              code
              current_balance {
                value
                currency
              }
              expiration_date
          }
        }
        status
      }
    }
  }
}
```

<u>Förväntade resultat</u>:

`total_giftcard` fältet är tillgängligt.

<u>Faktiska resultat</u>:

Inga presentkortsrelaterade fält är tillgängliga.

## Tillämpa korrigeringen

Om du vill använda enskilda korrigeringsfiler använder du följande länkar beroende på distributionsmetod:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html).

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Mer information om andra korrigeringsfiler som finns i QPT-verktyget finns i [Patchar tillgängliga i QPT-verktyget](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) -avsnitt.
