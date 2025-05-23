---
title: Återställa Adobe Commerce som fastnat i cron-jobb för molninfrastruktur manuellt
description: Adobe Commerce på molninfrastrukturcron-jobb slutför inte körningen, fastnar och förhindrar att andra kronijobb körs. I den här artikeln visas hur du återställer de fastnade kron-jobben manuellt.
exl-id: aec6de8e-c3a9-4a6d-8ecd-a213e77c97a1
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Återställa Adobe Commerce som fastnat i cron-jobb för molninfrastruktur manuellt

Adobe Commerce på molninfrastrukturcron-jobb slutför inte körningen, fastnar och förhindrar att andra kronijobb körs. I den här artikeln visas hur du återställer de fastnade kron-jobben manuellt.

Använd det här kommandot med försiktighet! Vi rekommenderar att du läser artikeln [Återställ cron-jobb](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=sv-SE) i vår kunskapsbas för support för mer information.

## Steg

>[!INFO]
>
>Från [ECE-Tools v2002.0.4](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-release-archive.html?lang=sv-SE#v2002.0.4) kan du manuellt återställa fastnade cron-jobb med ett CLI-kommando via SSH-åtkomst.

1. [SSH till din miljö](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=sv-SE).
1. Kör det här kommandot: `./vendor/bin/ece-tools cron:unlock`

## Varningar

* Kommandot återställer **alla** cron-jobb, inklusive de som körs för närvarande. **Använd det bara i undantagsfall**.
* Undvik att använda den här lösningen när indexerare körs.

## Läs det i vår kunskapsbas:

[Återställ cron-jobb](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=sv-SE)
