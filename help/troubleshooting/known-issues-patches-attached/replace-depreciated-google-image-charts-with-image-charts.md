---
title: Ersätt avskrivna Google Image Charts med Image-Charts
description: De flesta utgåvor och versioner av Adobe Commerce använder för närvarande [Google Image Charts](https://developers.google.com/chart/image/) för att återge statiska diagram på Admin-paneler. Från och med den 14 mars 2019 upphör Google att stödja Google Image Charts. För att lösa problemet tillhandahåller vi en patch som ersätter Google Image Charts med den kostnadsfria tjänsten [Image-Charts](https://www.image-charts.com/).
exl-id: f86f0bb9-8a03-471d-8696-1eba4b8acbd1
feature: Cache, Compliance
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# Ersätt avskrivna Google Image Charts med Image-Charts

De flesta utgåvor och versioner av Adobe Commerce använder för närvarande [Google Image Charts](https://developers.google.com/chart/image/) för att återge statiska diagram på Admin-paneler. Från och med den 14 mars 2019 upphör Google att stödja Google Image Charts. För att lösa det här problemet tillhandahåller vi en patch som ersätter Google Image Charts med den kostnadsfria tjänsten [Image-Charts](https://www.image-charts.com/).

## Berörda versioner

* Adobe Commerce 1.X, alla utgåvor
* Adobe Commerce 2.X, alla utgåvor

>[!NOTE]
>
>Den här diagramuppdateringen kommer att ingå i Adobe Commerce lokalt 1.14.4.1, Magento Open Source 1.9.4.1, Adobe Commerce lokalt och Adobe Commerce i molninfrastruktur 2.3.2. Uppgradering till dessa versioner fortsätter att ha stöd för bilddiagram utan ytterligare korrigeringar.

## Problem

Google slutade stödja Google Image Charts den 14 mars 2019. Användare av Adobe Commerce 1.X och Adobe Commerce 2.2.X av alla versioner kan inte visa statiska diagram om de inte laddar ned och installerar patchen och ersätter Google Image Charts med Image-Charts-lösningen. Visade diagram har samma utformning och funktionalitet som Google Image Charts via den kostnadsfria kontotjänsten Image-Charts med en [GDPR](https://www.image-charts.com/data-processing-addendum.html) -integritetspolicy. Mer information finns i [Bildscheman](https://www.image-charts.com/).

## Lösning

Om du vill kunna visa statiska diagram i Commerce Admin hämtar och installerar du patchen som tillhandahålls av Adobe Commerce. Ingen ytterligare konfiguration behövs.

### Adobe Commerce lokalt

1. Spara patchen [attached MAGETWO-98833\_Composer\_patch-2019-04-15-04-38-57.patch](assets/MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch.zip) och överför den till Adobe Commerce rotkatalog.
1. Kör följande SSH-kommando när du har ersatt korrigeringsnamnet med det faktiska:

   ```git
   patch -p1 < MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch
   ```

   Om ovanstående kommando inte fungerar kan du försöka med att använda `-p2` i stället för `-p1`.)

1. Uppdatera cacheminnet i administratören under **System** > **Cachehantering** för att ändringarna ska återspeglas.

### Adobe Commerce i molninfrastruktur

För molnhandlare kommer patchen att ingå i den närmaste uppdateringen av ECE-verktygen.

### Magento 2 Open Source

1. Gå till [https://magento.com/tech-resources/download\#download2291](https://magento.com/tech-resources/download#download2291).
1. I listrutan **Välj format** markerar du dispositionsversionen och klickar på **Hämta**.
1. Överför patchen till Adobe Commerce rotkatalog.
1. Kör följande SSH-kommando när du har ersatt korrigeringsnamnet med det faktiska:

   ```git
   patch -p1 < MAGETWO-98833_composer_patch-2019-04-15-04-37-48.patch
   ```

   (Om ovanstående kommando inte fungerar kan du försöka med att använda `-p2` i stället för `-p1`.)

1. Uppdatera cacheminnet i administratören under **System** > **Cachehantering** för att ändringarna ska återspeglas.

### Lokal Adobe Commerce 1

Följ de här stegen för att hämta och använda korrigeringen:

1. Spara patchen [attached MPERF-10509-EE-2019-03-13-06-32-19.diff](assets/MPERF-10509-EE-2019-03-13-06-32-19.diff.zip) och överför den till Adobe Commerce rotkatalog.
1. Kör följande SSH-kommando:

   ```git
   patch -p1 < MPERF-10509-EE-2019-03-13-06-32-19.diff
   ```

   (Om ovanstående kommando inte fungerar kan du försöka med att använda `-p2` i stället för `-p1`.)

1. Uppdatera cacheminnet i administratören under **System** > **Cachehantering** för att ändringarna ska återspeglas.

### Magento 1 Open Source

Följ de här stegen för att hämta och använda korrigeringen:

1. Klicka på [**den här länken**](https://magento.com/tech-resources/download#download2283) för att hitta uppdateringen Admin Dashboard Charts.
1. Välj

   ```git
   MPERF-10509.diff
   ```

   från listrutan **Välj format** och klicka på Hämta.

1. Överför filen till Adobe Commerce rotkatalog.
1. Kör följande SSH-kommando:

   ```git
   patch -p1 < MPERF-10509.diff
   ```

   (Om ovanstående kommando inte fungerar kan du försöka med att använda `-p2` i stället för `-p1`.)

1. Uppdatera cacheminnet i administratören under **System** > **Cachehantering** för att ändringarna ska återspeglas.

## Bifogade filer

[Ladda ned MAGETWO-98833_Composer_patch-2019-04-15-04-38-57.patch](assets/MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch)

[Hämta MPERF-10509-EE-2019-03-13-06-32-19.diffh](assets/MPERF-10509-EE-2019-03-13-06-32-19.diff)
