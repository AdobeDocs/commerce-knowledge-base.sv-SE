---
title: 'MDVA-40830: Butikskrediten tillämpas flera gånger under beställningen'
description: MDVA-40830-korrigeringen åtgärdar ett problem där butikskrediten tillämpas flera gånger under orderplaceringen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 är installerat. Korrigerings-ID är MDVA-40830. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 218a100a-4500-4ef5-bbdb-fbbd12f2fa26
feature: Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-40830: Butikskrediter som tillämpas flera gånger under beställningen

MDVA-40830-korrigeringen åtgärdar ett problem där butikskrediten tillämpas flera gånger under orderplaceringen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 är installerat. Korrigerings-ID är MDVA-40830. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.3.7-p2, 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Butikskrediten tillämpas flera gånger under orderplaceringen.

<u>Steg som ska återskapas</u>:

1. Skapa en kund och lägg till butikskrediter till kundkontot.
1. Lägg en enkel produkt i kundvagnen.
1. Ange leveransadress och faktureringsadress för vagnen.
1. Kontrollera kundvagnens totalsumma.
1. Använd butikskrediten i kundvagnen på följande GraphQL-begäran:

<pre>
<code class="language-graphql">
mutation {
  applyStoreCreditToCart(
    input: { cart_id: "%cartId%" }
  ) {
    cart {
      prices {
        grand_total {
          currency
          value
        }
      }
      applied_store_credit {
        applied_balance {
          currency
          value
        }
        current_balance {
          currency
          value
        }
      }
    }
  }
}
</code>
</pre>

<u>Förväntade resultat</u>:

Värdet för applied_store_credit tillämpas korrekt och kundvagnssummorna återspeglas korrekt i API-svaret.

<u>Faktiska resultat</u>:

Värdet för applied_store_credit används två gånger, vilket påverkar både kundvagnen och totalsumman.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
