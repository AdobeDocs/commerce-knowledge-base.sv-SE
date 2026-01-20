---
title: Databasfel relaterade till max_allowed_packet på Adobe Commerce
description: I den här artikeln finns en lösning för databasanslutningsfel i "var/log/exception.log" som kan uppstå när ett stort antal produkter importeras eller en annan åtgärd som tvingar servern att hantera större paket än vad som angetts i "max_allowed_packet" som är större än standardvärdet, 16 MB.
exl-id: e8932b72-91a3-43ea-800e-a6c7a5a17656
feature: Best Practices, Observability, Services
role: Developer
source-git-commit: 5ca7a4400e62db2419b32a31a4f6cf04f5a82e35
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Databasfel relaterade till max_allowed_packet på Adobe Commerce

Den här artikeln innehåller en lösning för databasanslutningsfel i `var/log/exception.log` som kan uppstå när ett stort antal produkter importeras eller en annan åtgärd som tvingar servern att hantera större paket än vad som angetts i `max_allowed_packet` som är större än standardvärdet, 16 MB.

## Berörda produkter och versioner

* Adobe Commerce lokalt, alla [versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

När en [!DNL MySQL]-klient eller [mysqld](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html)-servern tar emot ett paket som är större än [max\_allowed\_package](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html#sysvar_max_allowed_packet) byte, genereras ett [ER\_NET\_PACKET\_TOO\_LARGE](https://dev.mysql.com/doc/mysql-errors/8.0/en/server-error-reference.html#error_er_net_packet_too_large) -fel (som visas i `exception.log`) och anslutningen stängs. Med vissa klienter kan du även få en *borttappad anslutning till [!DNL MySQL]-servern under ett fråge*-fel om kommunikationspaketet är för stort.

<u>Steg som ska återskapas</u>

En mängd olika uppgifter kan ge upphov till det här problemet. Det kan vara att försöka importera ett stort antal produkter till Adobe Commerce eller transaktionsfrågor som skickar tillbaka för mycket data. Resultatet är databasanslutningsfel i `var/log/exception.log` och andra problem, till exempel att produkter inte kan importeras.

## Orsak

Standardvärdet 16 MB för inställningen [!DNL MySQL] `max_allowed_packets` är inte tillräckligt stort för dina behov.

## Lösning

1. Identifiera frågor där de enskilda raderna överskrider den aktuella `max_allowed_packet`-gränsen. Sådana frågor måste skrivas om för att minska mängden data som returneras. Detta kan du göra genom att ha ett mindre antal kolumner i programsatsen `SELECT` eller välja en mindre datatyp för olika kolumner som en del av tabelldesignen. Om du har ett New Relic-konto använder du [New Relic APM-felsida](https://docs.newrelic.com/docs/apm/apm-ui-pages/error-analytics/errors-page-explore-events-behind-errors) och [New Relic APM-databaser](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time) samt [New Relic-loggar](https://docs.newrelic.com/docs/logs/log-management/get-started/get-started-log-management) för att söka efter relevanta frågor.
1. För att åtgärda detta snabbt kan du tillfälligt begära att storleken på `max_allowed_packet` ökas när du [skickar in en biljett](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), men det är kundkonstruktörsteamets val, eftersom ett för stort värde kan orsaka replikeringsfel genom att orsaka nätverksproblem.
1. Det är en god idé att köra följande kommando i CLI för några av de stora databastabellerna:

   ```
   show table status like [table name to match]
   ```

   Utvärdera de frågor som körs i de här tabellerna för att avgöra om du överskrider den rekommenderade storleken på `max_allowed_packet` på 16 MB. Följ samma process i steg ett för att minska antalet data som returneras av sådana frågor.

## Relaterad läsning

* [Lokal installationsöversikt](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/overview) i utvecklardokumentationen.
* [Databasera bästa praxis för Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=sv-SE) i vår kunskapsbas för support.
* [Bästa tillvägagångssätt för att lösa databasprestandaproblem](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html?lang=sv-SE) i vår kunskapsbas för support.
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
