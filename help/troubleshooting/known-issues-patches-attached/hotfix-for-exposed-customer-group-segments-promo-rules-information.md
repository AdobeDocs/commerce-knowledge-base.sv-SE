---
title: Information om kundgruppsnamn, segment och kampanjregler som visas via  [!DNL GraphQL]
description: Den här artikeln innehåller en snabbkorrigering som förhindrar exponering av kundgruppsnamn, kundsegment och kampanjregelinformation via  [!DNL GraphQL].
feature: GraphQL
role: Admin, Developer
source-git-commit: f32085c80c9dbce513dad15ebf5f77a0e6398466
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# Information om kundgruppsnamn, segment och kampanjregler som visas via [!DNL GraphQL]

Den här artikeln innehåller en snabbkorrigering som förhindrar exponering av kundgruppsnamn, kundsegment och kampanjregelinformation via [!DNL GraphQL]. Problemet är schemalagt att åtgärdas i Adobe Commerce 2.4.8-p1.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.8

## Problem

För [!UICONTROL Storefront Personalization Drop-ins] introducerades nya [!DNL GraphQL]-mutationer för att visa grundläggande information som kundgruppsnamn, segment, kundvagn och katalogregler. Detta kan emellertid visa känsliga data, t.ex. erbjudandeinformation eller kupongkoder, om de ingår i namnen.

### Steg som ska återskapas

#### Fall I: [!UICONTROL Catalog Rule]

1. Gå till **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]** på sidofältet *Admin*.
1. Definiera regelvillkoren (till exempel produktattribut eller kategori).
1. Spara och använd regeln.
1. Se till att en produkt uppfyller regelvillkoren.
1. Kör följande [!DNL GraphQL]-fråga för att hämta alla regler:

   ```
   query {
       allCatalogRules {
           name
       }
   }
   ```

1. Fråga en produkt för att verifiera om regeln gäller:

   ```
   query {
       products(filter: { sku: { eq: "product-sku" } }) {
           items {
               name
               rules {
                   name
               }
           }
       }
   }
   ```

#### Fall II: [!UICONTROL Cart Rule]

1. Gå till **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rule]** > **[!UICONTROL Add New Rule]** på sidofältet *Admin*.
1. Ange villkor som minsta kundvagnsvärde och kundgrupp.
1. Spara och använd regeln.
1. Lägg till produkter i kundvagnen för att utlösa regeln.
1. Använd [!DNL GraphQL] för att verifiera alla kundvagnsregler:

   ```
   query {
       allCartRules {
           name
       }
   }
   ```

1. Kontrollera om regler har tillämpats på den aktiva kundvagnen:

   ```
   query {
       cart(cart_id: "your-cart-id") {
           rules {
               name
           }
       }
   }
   ```

#### Fall III: [!UICONTROL Customer Group]

1. Gå till **[!UICONTROL Customers]** > **[!UICONTROL Customer Groups]** på sidofältet *Admin*.
1. Kontrollera att de förväntade grupperna finns.
1. Använd [!DNL GraphQL] för att hämta alla grupper:

   ```
   query {
       allCustomerGroups {
           name
       }
   }
   ```

1. Verifiera kundens/gästens grupp:

   ```
   query {
       customerGroup {
           name
       }
   }
   ```

#### Fall IV: [!UICONTROL Customer Segment] (endast för Adobe Commerce)

1. Gå till **[!UICONTROL Customers]** > **[!UICONTROL Customer Segments]** → **[!UICONTROL Add Segment]** på sidofältet *Admin*.
1. Definiera kundbaserade villkor (t.ex. order, kundvagnsinnehåll).
1. Tilldela relevant omfång: *[!UICONTROL Visitor]*, *[!UICONTROL Registered]* eller båda.
1. Se till att villkoren matchar en testkund.
1. Använd [!DNL GraphQL] för att kontrollera alla segment:

   ```
   query {
       allCustomerSegments {
           name
           apply_to
       }
   }
   ```

1. Validera de segment som används i en kundvagn:

   ```
   query {
       customerSegments(cartId: "your-cart-id") {
           name
       }
   }
   ```

<u>Förväntat resultat</u>:

Namn på kundgrupper, segment och kampanjregelinformation visas inte via [!DNL GraphQL].

<u>Faktiskt resultat</u>:

Namn på kundgrupper, segment och kampanjregelinformation visas via [!DNL GraphQL].

## Lösning

Använd de bifogade patcharna beroende på vilken version av Adobe Commerce du har:

* För Adobe Commerce version 2.4.8:

   * [LYNX-839_CE_2.4.8.patch](assets/LYNX-839_CE_2.4.8.patch.zip)
   * [LYNX-839_EE_2.4.8.patch](assets/LYNX-839_EE_2.4.8.patch.zip)

* För [!DNL Magento] Open Source version 2.4.8:

   * [LYNX-839_CE_2.4.8.patch](assets/LYNX-839_CE_2.4.8.patch.zip)
