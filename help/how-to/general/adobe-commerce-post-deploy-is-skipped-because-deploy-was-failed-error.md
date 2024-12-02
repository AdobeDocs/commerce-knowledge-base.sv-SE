---
title: Adobe Commerce *post-deploy hoppas över eftersom distributionen misslyckades*-fel
description: 'I den här artikeln beskrivs hur du undersöker ett distributionsfel: *Efter distributionen hoppas över eftersom distributionen misslyckades*'
exl-id: cd0a3015-b7b9-442e-8ac1-89447ef12cd7
feature: Deploy
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Adobe Commerce *efter distributionen hoppas över eftersom distributionen misslyckades*-fel

I den här artikeln beskrivs hur du undersöker ett distributionsfel: *Efterdistributionen hoppas över eftersom distributionen misslyckades*, vilket inträffar under distributionen till olika miljöer, till exempel uppgradering.

## Berörda produkter och versioner

Adobe Commerce i molninfrastrukturen [alla versioner som stöds](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problem

Distributionen misslyckas och returnerar ett generiskt felmeddelande, så det är inte klart hur felet ska lösas.

## Orsak

Odefinierad - vad som orsakar det här felmeddelandet beror på koden och databasen som distribueras.

## Undersöka distributionsfelet

```
[20XX-XX-XX XX:XX:XX] DEBUG: Running step: is-deploy-failed
    W:
    W: In Processor.php line 129:
    W:
    [20XX-XX-XX XX:XX:XX] ERROR: [201] Post-deploy is skipped because deploy was failed.
    W:   Post-deploy is skipped because deploy was failed.
    W:
    W:
    W: In DeployFailed.php line 39:
    W:
    W:   Post-deploy is skipped because deploy was failed.
    W:
    W:
    W: post-deploy
    W:
```

Om du vill få felspårningen för att fastställa den faktiska orsaken, skickar du SSH till servern och kontrollerar loggfilen `var/log/install_upgrade.log`.
