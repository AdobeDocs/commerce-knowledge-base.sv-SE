---
title: Nya kunder visas inte i kundrutnätet efter CSV-import
description: I den här artikeln finns en korrigering av problemet när du inte kan se nya kunder under **Kunder** &gt; **Alla kunder** efter en import från en .csv-fil. Lösningen är att ställa in indexeraren "customer_grid" till "Update on Save" och manuellt indexera om kundrutnätet.
exl-id: e4d9d60a-a0d1-4602-924e-a338e56de61d
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Nya kunder visas inte i kundrutnätet efter CSV-import

Den här artikeln innehåller en korrigering av problemet när du inte kan se nya kunder under **Kunder** > **Alla kunder** efter en import från en `.csv`-fil. Lösningen är att ställa in indexeraren `customer_grid` på läget&quot;Uppdatera vid spara&quot; och manuellt indexera om kundstödrastret.

## Berörda versioner

* Adobe Commerce lokal 2.2.0 och senare
* Adobe Commerce om molninfrastruktur 2.2.0 och senare

## Problem

När du har importerat nya kunder från en `.csv`-fil med den inbyggda Adobe Commerce-importfunktionen kanske du inte kan se de nya kundposterna under **Kunder** > **Alla kunder** i Admin förrän du indexerar om `customer_grid`-indexeraren manuellt.

## Orsak

Indexeringsläget Uppdatera vid schema i Adobe Commerce 2.2.0 och senare stöder inte indexeraren `customer_grid` på grund av prestandaproblem.

## Lösning

Konfigurera `customer_grid`-indexeraren så att den indexeras om med läget Uppdatera vid spara. Gör så här:

1. Logga in på Commerce Admin.
1. Klicka på **System** > **Verktyg** > **Indexhantering**.
1. Markera kryssrutan bredvid indexeraren för kundstödraster.
1. Välj *Uppdatera vid Spara* i listrutan **Åtgärder**.
1. Klicka på **Skicka**.

Vi rekommenderar även att du indexerar om indexeraren `customer_grid` manuellt efter att du har konfigurerat indexeringsläget för att se till att indexet är uppdaterat och kan fungera med cron. Använd följande kommando om du vill indexera om manuellt:

`bin/magento indexer:reindex customer_grid`

## Mer information

Länkar till relaterade ämnen i vår utvecklardokumentation:

* [Indexeringsöversikt](https://developer.adobe.com/commerce/php/development/components/indexing/)
* [Hantera indexerare](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/cli/manage-indexers)
