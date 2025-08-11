---
title: Kontrollera loggar för att felsöka 500- och 503-fel på Adobe Commerce
description: I den här artikeln beskrivs hur du kontrollerar "access.log" och relaterade loggar för att felsöka 503- och 500-fel, som kan orsakas av trafik eller otillräckliga serverresurser. Om du visar loggarna "access.log" och relaterade loggar kan du få information om vad som kan orsaka problem med Adobe Commerce i molninfrastrukturen.
exl-id: 47d7de6b-3e12-4e79-a5c1-c27a9196b99c
feature: Cloud, Logs
source-git-commit: 66ac9de94e9a4a1eccdb5aac1875ecf0a0637e90
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Kontrollera loggar för att felsöka 500- och 503-fel på Adobe Commerce

I den här artikeln beskrivs hur du kontrollerar `access.log` och relaterade loggar för att felsöka 503- och 500-fel, som kan orsakas av trafik eller otillräckliga serverresurser. Om du visar `access.log` och relaterade loggar kan du få information om vad som kan orsaka problem med Adobe Commerce i molninfrastrukturen.

<!--
Bob - not in TOC
-->

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen, alla [versioner som stöds](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html).

Om du vill visa loggar för dessa serverfel kontrollerar du `access.log` på webbservern, t.ex. `<ip address>` `<timestamp>` `<request uri>` `<response code>` `<referer url>`

Så här kontrollerar du relaterade loggar:

1. Kör följande kommando i CLI om det är på den aktuella dagen (för Adobe Commerce på Cloud Infrastructure Pro-planarkitekturen). Eller upp till en viss tidpunkt (för Adobe Commerce i molninfrastrukturens startplanarkitektur), eftersom loggarnas varaktighet är begränsad och loggrotation inte är tillgänglig: `grep -r "\" [50[0-9]" /path/to/access.log` Om felet har inträffat tidigare kör du följande kommando i CLI (endast Pro-arkitekturen): `zgrep "\" 50[0-9]" /path/to/access.log.<rotation ID>.gz`
1. Kontrollera sedan `exception.log` och `error.log` eller motsvarande [roterad logg](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#log-rotation) (loggar som automatiskt roteras och komprimeras när de når en viss filstorlek) för samma tidsstämpel för att se vad som kan ha orsakat det. Obs! Om du vill kontrollera `exception.log` och `error.log` kör du ovanstående kommandon i CLI men ersätter `access.log` med `exception.log` eller `error.log`.

## Relaterad läsning

* Se [Visa och hantera loggar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) i *Adobe Commerce on Cloud Infrastructure Guide*.
* Se [Felsökning av 503 fel](/help/troubleshooting/miscellaneous/troubleshooting-503-errors.md) i vår kunskapsbas för support.