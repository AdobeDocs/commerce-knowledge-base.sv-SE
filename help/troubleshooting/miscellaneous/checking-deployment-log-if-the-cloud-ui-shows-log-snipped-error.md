---
title: Kontrollerar distributionsloggen om molnanvändargränssnittet har fel av typen"loggutdragen"
description: I den här artikeln finns en lösning på problemet där användargränssnittet i Adobe Commerce för molninfrastruktur visar *-loggen som klippts ut eftersom den var för lång* när du försökte visa distributionsloggen i molnprojektgränssnittet.
exl-id: 04d28741-72c1-4722-be46-425fe136b9a6
feature: Cloud, Deploy, Logs, Paas
role: Developer
source-git-commit: 71bec5b99063d771982f6dcab111b9e5a4aaec69
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Kontrollerar distributionsloggen om molngränssnittet har *loggutdraget* fel

I den här artikeln finns en lösning på problemet där Adobe Commerce i molninfrastruktursgränssnittet visar *loggen som klippts ut eftersom den var för lång* när ett försök gjordes att visa distributionsloggen i molnprojektets användargränssnitt. (Gäller inte [Adobe Commerce Cloud Console](https://console.adobecommerce.com/).)

## Berörda produkter

Adobe Commerce om molninfrastruktur (alla versioner som stöds)

## Problem

När du försöker visa distributionsloggen i molnprojektgränssnittet visas följande felmeddelande i Adobe Commerce i molninfrastrukturgränssnittet: *loggen har klippts ut eftersom den var för lång*.

## Steg som ska återskapas

1. Gå till Project URL och klicka på **Status** för den aktuella distributionen.
1. Om loggen är för lång för att visas i användargränssnittet visas felmeddelandet: *log snipped (loggning) eftersom den var för lång*.

## Orsak

Observera att loggen som visas i användargränssnittet inte ska behandlas som en källa till sanningen, särskilt om du upptäcker att webbplatsen inte svarar eller fungerar som den ska efter att distributionen hade statusen Slutfört. Du bör även verifiera med loggarna på servern. Se [Visa och hantera loggar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) i utvecklardokumentationen.

## Lösning

1. Kontrollera att du har [Magento Cloud CLI](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html) installerat i din lokala miljö.
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

* [Adobe Commerce i molninfrastruktur > Skapa och distribuera](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html)
* [Adobe Commerce i molninfrastruktur > Visa och hantera loggar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)
