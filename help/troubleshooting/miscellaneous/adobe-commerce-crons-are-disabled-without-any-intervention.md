---
title: Adobe Commerce [!DNL crons] inaktiverad utan åtgärd
description: Använd den här artikeln för att åtgärda problemet där [!DNL crons] inaktiveras utan åtgärd.
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
source-git-commit: 9cd7cabc37c0f290c41f790b0fb06177c3156d48
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Adobe Commerce crons inaktiverade utan åtgärd

Den här artikeln innehåller en lösning för när [!DNL crons] inaktiveras utan åtgärd.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen, alla [versionerna](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Problem

Dina [!DNL crons] inaktiveras efter distributionen.

<u>Steg som ska återskapas</u>:

Driftsätt.

<u>Förväntat resultat</u>:

Dina [!DNL crons] är igång.

<u>Faktiskt resultat</u>:

Dina [!DNL crons] inaktiveras efter distributionen.

## Orsak

Ett problem med [!DNL OPcache] inställningar.

## Lösning

Uppgradera [!DNL ECE Tools] till den senaste versionen [2002.1.13](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html#v2002113).

## Relaterad läsning

* [Långsam prestanda, långsam och långsam [!DNL crons]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.html) i vår kunskapsbas för support.
* [[!DNL Cron] uppgifter låsa uppgifter från andra grupper](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=en) i vår kunskapsbas för support.
* [[!DNL Cron] jobbet har fastnat i statusen&quot;kör&quot;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) i vår kunskapsbas för support.
