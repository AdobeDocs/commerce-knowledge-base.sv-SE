---
title: Kontrollerar distributionsloggen om molnanvändargränssnittet har fel av typen"loggutdragen"
description: I den här artikeln finns en lösning på problemet där användargränssnittet i Adobe Commerce för molninfrastruktur visar *-loggen som klippts ut eftersom den var för lång* felmeddelande när distributionsloggen skulle visas.
exl-id: 04d28741-72c1-4722-be46-425fe136b9a6
feature: Cloud, Deploy, Logs, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Kontrollerar distributionsloggen om molnanvändargränssnittet har fel av typen&quot;loggutdragen&quot;

Den här artikeln innehåller en lösning på problemet där användargränssnittet i Adobe Commerce för molninfrastruktur visar *loggen har klippts av eftersom den var för lång* felmeddelande när distributionsloggen visas.

## Berörda produkter

Adobe Commerce om molninfrastruktur (alla versioner som stöds)

## Problem

När du försöker visa distributionsloggen visas följande felmeddelande i användargränssnittet för molninfrastruktur: *loggen har klippts av eftersom den var för lång*.

## Steg som ska återskapas

1. Gå till Project URL och klicka på **Status** av den aktuella driftsättningen.
1. Om loggen är för lång för att visas i användargränssnittet visas felmeddelandet: *loggen har klippts av eftersom den var för lång*.

## Orsak

Observera att loggen som visas i användargränssnittet inte ska behandlas som en källa till sanningen, särskilt om du upptäcker att webbplatsen inte svarar eller fungerar som den ska efter att distributionen hade statusen Slutfört. Du bör även verifiera med loggarna på servern. Se [Visa och hantera loggar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) i vår dokumentation för utvecklare.

## Lösning

1. Se till att du har [Magento Cloud CLI](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html) installeras i din lokala miljö.
1. Kör följande kommando:

   ```bash
   magento-cloud activity -p <project id> -e <environment>
   ```

1. Den returnerar utdata som liknar följande:

   ```bash
   Activities on the project <project name> (project id), environment <environment>:
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | ID            | Created                   | Description                         | Progress | State    | Result  |
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | l5wgwmzwrsskg | 2021-06-01T08:18:02-07:00 | ABC merged Integration into Staging | 100%     | complete | success |
   | raah5xrhqz3wg | 2021-06-01T08:07:18-07:00 | XYZ pushed to Integration           | 100%     | complete | failure |
   ```

1. Kopiera aktivitets-ID för den aktuella distributionen och kör sedan kommandot:

   ```bash
   magento-cloud activity:log <activity ID> -p <project id> -e <environment>
   ```

   Exempel på att undersöka loggen för den misslyckade distributionen:

   ```bash
   magento-cloud activity:log raah5xrhqz3wg -p <project id> -e <environment>
   ```

## Relaterade läsningar i vår dokumentation för utvecklare:

* [Adobe Commerce i molninfrastruktur > Bygg och driftsätt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html)
* [Adobe Commerce i molninfrastruktur > Visa och hantera loggar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)
