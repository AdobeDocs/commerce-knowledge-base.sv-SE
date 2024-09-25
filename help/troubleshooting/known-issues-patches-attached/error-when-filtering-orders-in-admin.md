---
title: Fel vid filtrering av order i administratören
description: I den här artikeln finns en patch för Adobe Commerce-problemet, där ett fel inträffar när du försöker filtrera order i Admin efter datum och meddelandet "Integritetsbegränsningsöverträdelse 1052 Kolumnen 'created_at' där -satsen är tvetydig" visas.
feature: Orders
role: Developer
source-git-commit: e5eb65b23afaed4658f8576c747f11a31a8ec1aa
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Fel vid filtrering av order i administratören

Den här artikeln innehåller en korrigering för Adobe Commerce-problemet där ett fel inträffar när försök görs att filtrera order i Admin efter datum. Meddelandet *Överträdelse av integritetsbegränsning: 1052 Kolumnen &#39;created_at&#39; där satsen är tvetydig* visas.

## Berörda versioner

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7

## Problem

Ett fel returneras när du filtrerar order i Admin efter datum.

Exception.log visar:

```SQL
report.CRITICAL: PDOException: SQLSTATE[23000]: Integrity constraint violation: 1052 Column 'created_at' in where clause is ambiguous in /path/to/magento/vendor/magento/framework/DB/Statement/Pdo/Mysql.php:90
```

<u>Steg att återskapa:</u>

1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
   * Ange **[!UICONTROL Purchase Date Ascending]**-ordning i rutnät, ELLER
   * Ange **[!UICONTROL Purchase Date Filter]** i filter.

1. Ett fel visas: *Ett fel uppstod när standardvyn bearbetades och vi har återställt filtret till det ursprungliga läget.*

## Orsak

Det har uppstått ett problem med modulerna [!DNL PayPal Braintree].

## Lösning

Du löser problemet genom att tillämpa den patch som är bifogad den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[bundle_3357_filter_order_in_admin_by_date_patch.zip](assets/bundle-3357-unable-to-filter-order-in-admin-by-date.zip)

Korrigeringen är kompatibel med alla berörda versioner och utgåvor.

## Så här sätter du på plåstret

Instruktioner finns i [Använda en dispositionsruta från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i kunskapsbasen med supportfrågor.
