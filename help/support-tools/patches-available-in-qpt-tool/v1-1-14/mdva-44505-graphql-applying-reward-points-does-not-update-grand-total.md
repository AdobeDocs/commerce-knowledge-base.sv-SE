---
title: 'MDVA-44505: GraphQL-fråga för kundvagn som tillämpar belöningspunkter uppdaterar inte totalsumman'
description: MDVA-44505-korrigeringen löser problemet där GraphQL-frågan för en kundvagn som tillämpar belöningspoäng inte tar hänsyn till belöningspoängen och returnerar ett felaktigt totalbelopp. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 är installerat. Patch-ID:t är MDVA-44505. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.
exl-id: 724273ba-b020-4dba-88ae-94968bbd83de
feature: GraphQL, Orders, Rewards, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-44505: GraphQL-fråga för kundvagnstillämpande belöningspunkter uppdaterar inte totalsumman

MDVA-44505-korrigeringen löser problemet där GraphQL-frågan för en kundvagn som tillämpar belöningspoäng inte tar hänsyn till belöningspoängen och returnerar ett felaktigt totalbelopp. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 är installerat. Patch-ID:t är MDVA-44505. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

I GraphQL-frågan för en kundvagn som tillämpar belöningspoäng tas inga hänsyn till belöningspoängen och en felaktig totalsumma returneras.

<u>Steg som ska återskapas</u>:

1. Konfigurera belöningspoäng.
1. Skapa en kundvagn och använd några belöningspoäng.
1. Anropa frågan `GetCart` från slutpunkten `GraphQL` och hämta kundvagnen:

   ```GraphQL
   query {
     cart(cart_id: "{CART_ID}") {
       prices {
         discounts {
           amount {
             value
           }
         }
         grand_total {
           value
         }
       }
     }
   }
   ```

1. Kontrollera totalposten.
1. Kontrollera kundens kundvagnssumma med hjälp av rest-API (`/rest/V1/carts/mine/totals`).

<u>Förväntade resultat</u>:

GraphQL-frågan för kundvagnen returnerar den korrekta totalsumman som tar hänsyn till belöningspoängen.

<u>Faktiska resultat</u>:

GraphQL-frågan tar inte hänsyn till belöningspoängen och returnerar en felaktig totalsumma.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i vår utvecklardokumentation.
