---
title: "Adobe Commerce 2.3.7-p1 known issue: outdated order total for PayPal"
description: "Den här artikeln innehåller en patch för ett känt fel i Adobe Commerce 2.3.7-p1: när du använder PayPal Checkout flera gånger får kunderna den tidigare beställda produkten i kundvagn i stället för den nya som de försöker beställa."
exl-id: ceb8f7ad-0cf7-4d42-aded-25d1dd947f5b
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Adobe Commerce 2.3.7-p1 Känt fel: inaktuell ordersumma för PayPal

Den här artikeln innehåller en patch för ett känt problem i Adobe Commerce 2.3.7-p1: när du använder PayPal Checkout flera gånger får kunderna den tidigare beställda produkten i kundvagn i stället för den nya som de försöker beställa.
Du kan hämta korrigeringen från den här artikeln och den är även tillgänglig via QPT (Quality Patches Tool).

## Berörda versioner

* Adobe Commerce (alla installationsalternativ) 2.3.7-p1
* Magento Open Source 2.3.7-p1

## Problem

När du gör en beställning med betalningsmetoden PayPal Express Checkout läggs den tidigare beställda köpta produkten till i beställningen i stället för den faktiska.

<u>Steg att återskapa:</u>

1. I butiken lägger du till valfri produkt i kundvagnen (produkt A, pris $50).
1. Klicka på vagnslänken för att öppna vagnen.
1. Klicka på knappen **PayPal-utcheckning**.
1. Använd dina PayPal-inloggningsuppgifter för att logga in på PayPal och skicka betalningen.
1. Slutför orderplaceringen på butikssidan.
1. Gå tillbaka till katalogen och lägg till en annan produkt (produkt B, pris $100) i kundvagnen.
1. Klicka på vagnslänken för att öppna vagnen.
1. Klicka på knappen **PayPal-utcheckning**.

<u>Faktiskt resultat:</u>

Produktpriset i varukorgen är 50 dollar istället för 100 dollar.<br/>
På butikssidan innehåller beställningen produkt A i stället för produkt B.

<u>Förväntat resultat:</u>

Produkt B läggs till i ordern.

## Lösning

Använd den patch som finns i den här artikeln.

## Lappa

Använd följande länk om du vill hämta en ZIP-fil som innehåller korrigeringen: [MC42674-Composer.patch.zip](assets/MC42674-composer.patch.zip).

### Kompatibla Adobe Commerce-versioner

* Adobe Commerce (alla installationsalternativ) 2.3.7-p1

## Tillämpa patcharna

1. Zippa upp den hämtade ZIP-filen.
1. Mer information finns i [Använda en dispositionsruta från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).
