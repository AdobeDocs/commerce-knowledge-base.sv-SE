---
title: Adobe Commerce [!DNL crons] inaktiverat utan åtgärd
description: Använd den här artikeln om du vill åtgärda problemet där  [!DNL crons]  är inaktiverat utan åtgärd.
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Adobe Commerce crons inaktiverade utan åtgärd

Den här artikeln innehåller en lösning för när [!DNL crons] inaktiveras utan åtgärd.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen, alla [versioner som stöds](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Problem

[!DNL crons] har inaktiverats efter distributionen.

<u>Steg som ska återskapas</u>:

Driftsätt.

<u>Förväntat resultat</u>:

[!DNL crons] körs.

<u>Faktiskt resultat</u>:

[!DNL crons] har inaktiverats efter distributionen.

## Orsak

Ett problem med inställningarna för [!DNL OPcache].

## Lösning

Uppgradera [!DNL ECE Tools] till den senaste versionen, [ 2002.1.13](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package#v2002113).

## Relaterad läsning

* [Långsam prestanda, långsam och långsam [!DNL crons]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.html?lang=sv-SE) i vår kunskapsbas för support.
* [[!DNL Cron] aktiviteter låser aktiviteter från andra grupper](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=sv-SE) i vår kunskapsbas för support.
* [[!DNL Cron] jobbet har fastnat i statusen&quot;kör&quot;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=sv-SE) i vår kunskapsbas för support.
