---
title: Cachelagrade bilder läses inte in efter 2.2.X- till 2.3.X-uppgradering
description: Den här artikeln innehåller en lösning på problemet med cachelagrade bilder som inte visas efter uppgradering från Adobe Commerce i molninfrastrukturen 2.2.X till 2.3.X.
exl-id: 3e6bd5aa-bd5d-4880-8b78-64f280647abe
feature: Cache, Upgrade
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Cachelagrade bilder läses inte in efter 2.2.X- till 2.3.X-uppgradering

Den här artikeln innehåller en lösning på problemet med cachelagrade bilder som inte visas efter uppgradering från Adobe Commerce i molninfrastrukturen 2.2.X till 2.3.X.

## Berörda versioner och utgåvor:

* Adobe Commerce on cloud infrastructure Pro plan architecture 2.2.X, 2.3.X

## Problem

När Adobe Commerce har uppgraderats från 2.2.X till 2.3.X är de cachelagrade produktbilderna inte tillgängliga och en 404-sida visas istället.

Problemet orsakas av den felaktiga Nginx-konfigurationsuppsättningen i `.magento.app.yaml`: `index.php` (eller ingen) används för platsen `"/media"` i stället för `passthru: /get.php`.

## Lösning

1. Kontrollera `.magento.app.yaml`-konfigurationsfilen på platsen `"/media"`. Rätt konfiguration ser ut så här:

   ```yaml
   "/media":
       root: "pub/media"
       allow: true
       scripts: false
       expires: 1y
       passthru: "/get.php"
   ```

1. Om `passthru` inte är inställt på `"/get.php"` och `expires` inte är inställt utför du följande steg.
1. Korrigera konfigurationsfilen.
   * Starter Plan: korrigera filen själv och skicka ändringarna vidare.
   * Proffsplan:
   * Integrering: korrigera filen själv och skicka ändringarna.
   * Mellanlagring och produktion: korrigera filen själv, skicka ändringarna och skapa en [Adobe Commerce-supportanmälan](https://experienceleague.adobe.com/sv/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) som den ska tillämpas på.

1. Aktivera Snabb bildoptimering i Commerce Admin (snabbast måste konfigureras före) enligt beskrivningen i <https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization>.

Om konfigurationen är korrekt, men problemet kvarstår, kan du fortsätta med undersökningen eller kontakta [Adobe Commerce Support](https://experienceleague.adobe.com/sv/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide).
