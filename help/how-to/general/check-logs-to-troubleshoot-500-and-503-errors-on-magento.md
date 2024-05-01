---
title: Kontrollera loggar för att felsöka 500- och 503-fel på Adobe Commerce
description: I den här artikeln beskrivs hur du kontrollerar "access.log" och relaterade loggar för att felsöka 503- och 500-fel, som kan orsakas av trafik eller otillräckliga serverresurser. Om du visar loggarna "access.log" och relaterade loggar kan du få information om vad som kan orsaka problem med Adobe Commerce i molninfrastrukturen.
exl-id: 47d7de6b-3e12-4e79-a5c1-c27a9196b99c
feature: Cloud, Logs
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# Kontrollera loggar för att felsöka 500- och 503-fel på Adobe Commerce

I den här artikeln beskrivs hur du kontrollerar `access.log` och relaterade loggar för att felsöka 503- och 500-fel, som kan orsakas av trafik eller otillräckliga serverresurser. Visa `access.log` och relaterade loggar kan ge information om vad som kan orsaka problem i samband med Adobe Commerce molninfrastruktur.

<!--
Bob - not in TOC
-->

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen, alla [versionerna](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html).

Om du vill visa loggar för dessa serverfel kontrollerar du `access.log` på webbservern, till exempel `<ip address>` `<timestamp>` `<request uri>` `<response code>` `<referer url>`

Så här kontrollerar du relaterade loggar:

1. Kör följande kommando i CLI om det är på den aktuella dagen (för Adobe Commerce på Cloud Infrastructure Pro-planarkitekturen). Eller fram till en viss tidpunkt (för Adobe Commerce i molninfrastrukturens arkitektur), eftersom loggarnas varaktighet är begränsad och loggrotationen inte är tillgänglig: `grep -r "\" [50[0-9]" /path/to/access.log` Om felet har inträffat tidigare kör du följande kommando i CLI (endast Pro-arkitekturen): `zgrep "\" 50[0-9]" /path/to/access.log.<rotation ID>.gz`
1. Kontrollera sedan `exception.log` och `error.log` eller motsvarande [roterad logg](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#log-rotation) (loggar som automatiskt roteras och komprimeras när de når en viss filstorlek) för samma tidsstämpel för att hitta det potentiella felet och se vad som kan ha orsakat det. Obs! Kontrollera `exception.log` och `error.log` kör kommandona ovan i CLI men ersätt `access.log` med `exception.log` eller `error.log`.

## Relaterad läsning

* Se [Visa och hantera loggar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) i *Infrastrukturhandbok för Adobe Commerce on Cloud*.
* Se [Felsökning av 503 fel](/help/troubleshooting/miscellaneous/troubleshooting-503-errors.md) i vår kunskapsbas för support.
* Se [Felsökaren Magento Site Down](/help/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.md) i vår kunskapsbas för support.
