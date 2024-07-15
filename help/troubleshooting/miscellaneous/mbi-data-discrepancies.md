---
title: 'MBI: Datakonflikter'
description: "Ser siffrorna i en viss rapport felaktiga ut? Ser du oväntade NULL-värden? Om du ser något som inte verkar riktigt rätt rekommenderar vi att du använder dessa resurser för att felsöka:"
exl-id: 2ecea990-7292-46c1-b6eb-75f0404aaf0b
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 0%

---

# MBI: Dataavvikelser

Ser siffrorna i en viss rapport felaktiga ut? Ser du oväntade NULL-värden? Om du ser något som inte verkar riktigt bra rekommenderar vi att du använder dessa resurser för att felsöka:

* [Checklista för diagnostisk diskrepans](/help/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.md)
* [Använda export för att identifiera dataavvikelser](/help/troubleshooting/miscellaneous/using-data-exports-to-pinpoint-discrepancies.md)

Vi rekommenderar även att du kontrollerar att rätt [replikeringsmetoder](https://docs.magento.com/mbi/data-analyst/data-warehouse-mgr/cfg-replication-methods.html) och [rechecks](https://docs.magento.com/mbi/data-analyst/data-warehouse-mgr/cfg-data-rechecks.html) har angetts för de tabeller och kolumner som är inblandade i avvikelsen. Observera att du behöver administratörsbehörighet för att komma åt replikeringsmetoden och för att kontrollera information igen.

## Jag behöver fortfarande hjälp!

Om rapporten fortfarande är felaktig, oroa dig inte - vårt supportteam hjälper gärna till! [Nå ut till oss](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) med följande information:

* Vad heter rapporten där du ser diskrepansen?
* Vilka värden i rapporten är felaktiga?
* Vilka värden förväntar du dig?
* Alla SQL-frågor eller annan logik som du använder

## Relaterad läsning

* [Beräknade kolumner](/help/how-to/general/mbi-creating-and-editing-advanced-calculated-columns.md)
* [Strukturella databasändringar](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/connecting/data-migration-services.html)
