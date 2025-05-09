---
title: Google Analytics inaktiveras efter distributionen
description: I det här avsnittet beskrivs en lösning på ett typiskt problem som du kan uppleva med Google Analytics under distributionen.
exl-id: ecf6a277-2dfa-45cf-b86f-9a27f39017f4
feature: Build, Deploy, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# Google Analytics inaktiveras efter distributionen

I det här avsnittet beskrivs en lösning på ett typiskt problem som du kan uppleva med Google Analytics under distributionen.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur, alla versioner

## Problem

När du distribuerar din kod mellan miljöer verifieras grenen `master/production/staging` av skript som skapas och distribueras, så att Google Analytics är aktiverat. När du distribuerar utvecklargrenar (eller underordnade) av master- till utvecklarmiljöer (Integration) inaktiveras Google Analytics av distributionsskriptet.

## Orsak

Detta är en funktion som ska säkerställa att utvecklardata och interaktioner inte skickas till eller spåras av Google Analytics.

## Lösning

Om du alltid vill att Google Analytics ska vara aktiverat anger du distributionsvariabeln `ENABLE_GOOGLE_ANALYTICS = true` enligt beskrivningen i [Distribuera variabler](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#enable_google_analytics) i utvecklardokumentationen.

>[!NOTE]
>
>Vi är medvetna om att den här artikeln fortfarande kan innehålla programtermer som är branschstandard och som vissa kan finna rasistiska, sexistiska eller förtryckande och som kan få läsaren att känna sig sårad, traumatiserad eller ovälkommen. Adobe arbetar med att ta bort dessa villkor från vår kod, dokumentation och användarupplevelse.
