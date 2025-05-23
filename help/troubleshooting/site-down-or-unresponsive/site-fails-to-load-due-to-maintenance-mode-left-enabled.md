---
title: Platsen kan inte läsas in på grund av att underhållsläge är aktiverat
description: "I den här artikeln finns en fix som du kan använda när webbplatsen inte läses in på grund av att underhållsläget är inaktiverat eller inte har inaktiverats automatiskt. Du kan få ett felmeddelande: *Tjänsten är tillfälligt otillgänglig Servern kan för tillfället inte hantera din begäran på grund av driftavbrott eller kapacitetsproblem.*"
exl-id: 77e01588-e135-4d24-a0c4-1a6ee123f4a8
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Platsen kan inte läsas in på grund av att underhållsläge är aktiverat

Den här artikeln innehåller en korrigering för när platsen inte läses in på grund av att underhållsläget inte är aktiverat eller inte har inaktiverats automatiskt. Du kan få ett felmeddelande: *Tjänsten är tillfälligt otillgänglig Servern kan för tillfället inte hantera din begäran på grund av avbrott i underhållet eller kapacitetsproblem.*

## Berörda versioner och produkter

* Adobe Commerce om molninfrastruktur 2.2.x, 2.3.x
* Adobe Commerce lokal 2.2.x, 2.3.x

## Problem

Underhållsläget är en del av distributionsprocessen. Om det har aktiverats automatiskt och inte har inaktiverats, eller om det handlaraktiverade underhållsläget manuellt och har glömt att inaktivera, kan det leda till en misslyckad distribution.

## Orsak

Om underhållsläget är aktiverat går det inte att läsa in platsen.

## Lösning

Kör följande kommando från CLI för att kontrollera statusen för det aktuella underhållsläget:

```
bin/magento maintenance:status
```

Om du vill inaktivera underhållsläge kör du följande kommando i CLI:

```
bin/magento maintenance:disable
```

## Relaterad läsning

Mer information om när underhållsläge ska användas finns i [Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i utvecklardokumentationen.
