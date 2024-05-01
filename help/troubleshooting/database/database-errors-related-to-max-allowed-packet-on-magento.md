---
title: Databasfel relaterade till max_allowed_packet på Adobe Commerce
description: I den här artikeln finns en lösning för databasanslutningsfel i "var/log/exception.log" som kan uppstå när ett stort antal produkter importeras eller en annan åtgärd som tvingar servern att hantera större paket än vad som angetts i "max_allowed_packet" som är större än standardvärdet, 16 MB.
exl-id: e8932b72-91a3-43ea-800e-a6c7a5a17656
feature: Best Practices, Observability, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Databasfel relaterade till max_allowed_packet på Adobe Commerce

Den här artikeln innehåller en lösning för databasanslutningsfel i `var/log/exception.log` som kan inträffa vid import av ett stort antal produkter eller vid en annan åtgärd som tvingar servern att hantera större paket än vad som angetts i `max_allowed_packet` som är större än standardvärdet, 16 MB.

## Berörda produkter och versioner

* Adobe Commerce lokalt, alla [versionerna](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

När en MySQL-klient eller [mysqld](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html) servern tar emot ett paket som är större än [max\_allowed\_packet](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html#sysvar_max_allowed_packet) byte, den utfärdar [ER\_NET\_PACKET\_TOO\_LARGE](https://dev.mysql.com/doc/mysql-errors/8.0/en/server-error-reference.html#error_er_net_packet_too_large) fel (som visas i `exception.log`) och stänger anslutningen. Med vissa kunder kan du också få en *Anslutningen till MySQL-servern bröts under frågan* fel om kommunikationspaketet är för stort.

<u>Steg som ska återskapas</u>

En mängd olika uppgifter kan ge upphov till det här problemet. Det kan vara att försöka importera ett stort antal produkter till Adobe Commerce eller transaktionsfrågor som skickar tillbaka för mycket data. Resultatet är databasanslutningsfel i `var/log/exception.log` och andra problem, som att produkter inte importeras korrekt.

## Orsak

Standardvärdet 16 MB för MySQL `max_allowed_packets` inställningen är inte tillräckligt stor för dina behov.

## Lösning

1. Identifiera frågor där de enskilda raderna överskrider den aktuella `max_allowed_packet` gräns. Sådana frågor måste skrivas om för att minska mängden data som returneras. Detta kan du göra genom att ha ett mindre antal kolumner i `SELECT` eller välja en mindre datatyp för olika kolumner som en del av tabelldesignen. Om du har ett New Relic-konto använder du [New Relic APM-felsida](https://docs.newrelic.com/docs/apm/apm-ui-pages/error-analytics/errors-page-explore-events-behind-errors) och [New Relic APM-databassida](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time)och [New Relic Logs](https://docs.newrelic.com/docs/logs/log-management/get-started/get-started-log-management) om du vill söka efter relevanta frågor.
1. Du kan tillfälligt begära att `max_allowed_packet` storlek som ska ökas när du [skicka en biljett](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), men det är kundkonstruktörsteamet som bestämmer detta eftersom för mycket av värdet kan orsaka replikeringsfel genom att orsaka nätverksstockning.
1. Det är en god idé att köra följande kommando i CLI för några av de stora databastabellerna:

   ```
   show table status like [table name to match]
   ```

   Utvärdera de frågor som körs i de här tabellerna för att avgöra om du överskrider de rekommenderade värdena `max_allowed_packet` storlek 16 MB. Följ samma process i steg ett för att minska antalet data som returneras av sådana frågor.

## Relaterad läsning

* [Installationshandbok > MySQL](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/mysql.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=max%20allowed%2016%20MB) i vår dokumentation för utvecklare.
* [Databasöverföringen förlorar anslutningen till MySQL](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md) i vår kunskapsbas för support.
* [Bästa databaspraxis för Adobe Commerce om molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) i vår kunskapsbas för support.
* [Bästa tillvägagångssätt för att lösa databasprestandaproblem](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) i vår kunskapsbas för support.
