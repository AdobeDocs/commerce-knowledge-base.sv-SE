---
title: Cachelagrade bilder läses inte in efter 2.2.X- till 2.3.X-uppgradering
description: Den här artikeln innehåller en lösning på problemet med cachelagrade bilder som inte visas efter uppgradering från Adobe Commerce i molninfrastrukturen 2.2.X till 2.3.X.
exl-id: 3e6bd5aa-bd5d-4880-8b78-64f280647abe
feature: Cache, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Cachelagrade bilder läses inte in efter 2.2.X- till 2.3.X-uppgradering

Den här artikeln innehåller en lösning på problemet med cachelagrade bilder som inte visas efter uppgradering från Adobe Commerce i molninfrastrukturen 2.2.X till 2.3.X.

## Berörda versioner och utgåvor:

* Adobe Commerce on cloud infrastructure Pro plan architecture 2.2.X, 2.3.X

## Problem

När Adobe Commerce har uppgraderats från 2.2.X till 2.3.X är de cachelagrade produktbilderna inte tillgängliga och en 404-sida visas istället.

Problemet orsakas av felaktig Nginx-konfiguration i `.magento.app.yaml`: `index.php` (eller ingen) används för `"/media"` plats i stället för `passthru: /get.php`.

## Lösning

1. Kontrollera `.magento.app.yaml` konfigurationsfil, på `"/media"` plats. Rätt konfiguration ser ut så här:

   ```yaml
   "/media":
       root: "pub/media"
       allow: true
       scripts: false
       expires: 1y
       passthru: "/get.php"
   ```

1. If `passthru` är inte inställd på `"/get.php"` och `expires` är inte inställt gör du följande.
1. Korrigera konfigurationsfilen.
   * Starter Plan: korrigera filen själv och skicka ändringarna vidare.
   * Proffsplan:
   * Integrering: korrigera filen själv och skicka ändringarna.
   * Mellanlagring och produktion: korrigera filen själv, överföra ändringarna och skapa en [Adobe Commerce supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) för att få det tillämpat.

1. Aktivera snabb bildoptimering i Commerce Admin (Admin måste ha konfigurerats tidigare) enligt beskrivningen i <https://devdocs.magento.com/guides/v2.3/cloud/cdn/fastly-image-optimization.html>.

Om konfigurationen är korrekt, men du fortfarande har problem, kan du fortsätta med undersökningen eller kontakta [Adobe Commerce Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
