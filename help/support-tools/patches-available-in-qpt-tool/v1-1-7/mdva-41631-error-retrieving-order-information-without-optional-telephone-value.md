---
title: 'MDVA-41631: Det gick inte att hämta orderinformation utan det valfria telefonvärdet'
description: MDVA-41631-korrigeringen åtgärdar ett problem där användare får felmeddelanden när de hämtar orderinformation utan att ange ett"telefonvärde" via GraphQL. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 är installerat. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: 94b0b918-c1f9-4f5d-8fcd-8b92a9ca8c59
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-41631: Fel vid hämtning av orderinformation utan &quot;telefonvärde&quot; (tillval)

MDVA-41631-korrigeringen åtgärdar ett problem där användare får felmeddelanden när de hämtar orderinformation utan att ange ett&quot;telefonvärde&quot; via GraphQL. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 har installerats. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det går inte att hämta orderinformation utan telefonnummer via GraphQL.

<u>Steg som ska återskapas</u>:

1. Gå till **Store** > **Konfiguration** > **Kunder** > **Kundkonfiguration** > **Alternativ för namn och adress** > **Visa telefonnummer** och ange telefonnumret som valfritt.
1. Gör en beställning med GraphQL API som inloggad kund.
   * Ange inte telefonnumret när du anger fakturerings- och leveransadress. Följ instruktionerna i [GraphQL självstudiekurs för utcheckning](https://devdocs.magento.com/guides/v2.4/graphql/tutorials/checkout/checkout-customer.html) i vår utvecklardokumentation.
1. Hämta ordern med GraphQL [customerOrders-frågan](https://devdocs.magento.com/guides/v2.4/graphql/queries/customer-orders.html).

<pre>
<code class="language-graphql">
{
  customer {
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}}){
        items{
          billing_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
shipping_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
        }
    }
  }
}
</code>
</pre>

<u>Förväntade resultat</u>:

Användarna får beställningsinformation.

<u>Faktiska resultat</u>:

Användarna får följande fel: *&quot;message&quot;: &quot;Internal server error&quot;,*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
