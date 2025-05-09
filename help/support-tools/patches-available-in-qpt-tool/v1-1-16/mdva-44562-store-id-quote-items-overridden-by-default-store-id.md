---
title: 'MDVA-44562: Butiks-ID för offertobjekt som åsidosatts av standardbutiks-ID'
description: Korrigeringen MDVA-44562 åtgärdar ett problem där standarbutiks-ID åsidosätter butiks-ID för offertobjekt för GraphQL-begäranden. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 är installerat. Korrigerings-ID är MDVA-44562. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
exl-id: 902bfc05-411d-4a6c-a6e8-cd7376629b0c
feature: Quotes
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-44562: Butiks-ID för offertobjekt som åsidosatts av standardbutiks-ID

Korrigeringen MDVA-44562 åtgärdar ett problem där standarbutiks-ID åsidosätter butiks-ID för offertobjekt för GraphQL-begäranden. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 är installerat. Korrigerings-ID är MDVA-44562. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Butiks-ID för offertobjekt åsidosätts av standardbutiks-ID för GraphQL-begäranden.

<u>Steg som ska återskapas</u>:

1. Skapa en ny butiksvy.
1. Skapa en ny enkel produkt med olika namn per butiksvy.
1. Skapa en ny kund.
1. Hämta kundauktoriseringstoken.

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. Skapa en ny offert för kunden med en auktoriseringstoken.

   ```GraphQL
   POST rest/default/V1/carts/mine
   ```

1. Lägg en produkt i kundvagnen.

   ```GraphQL
   POST /rest/default/V1/carts/mine/items
   {
     "cartItem": {
       "sku": "simple1",
       "qty": 1,
       "quote_id": "1"
     }
   }
   ```

1. Hämta kundvagnsinnehållet för standardbutiksvyn.

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. Hämta kundvagnsinnehållet för den nya butiksvyn.

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u>Förväntade resultat</u>:

Svar från den nya butiksvyn visar produktnamnet från den nya butiksvyn.

<u>Faktiska resultat</u>:

Svar från den nya butiksvyn visar produktnamnsinställningarna under standardbutiksvyn.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i vår utvecklardokumentation.
