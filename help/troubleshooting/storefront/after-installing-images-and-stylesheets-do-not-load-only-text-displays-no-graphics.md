---
title: Efter installationen läses inte bilder och formatmallar in; endast textvisning, ingen grafik
description: I den här artikeln beskrivs möjliga orsaker och lösningar till problemet där formatmallar och bilder inte läses in efter installation av Adobe Commerce.
exl-id: f33cee89-b416-4d63-8cc5-9cc57618ce92
feature: Install, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# Efter installationen läses inte bilder och formatmallar in; endast textvisning, ingen grafik

I den här artikeln beskrivs möjliga orsaker och lösningar till problemet där formatmallar och bilder inte läses in efter installation av Adobe Commerce.

## Berörda produkter och versioner

* Adobe Commerce 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Problem

<u>Steg som ska återskapas</u>

1. Installera Adobe Commerce.
1. Navigera till butiken eller administratören.

<u>Förväntat resultat</u>

Format används. Inget gränssnittselement ser ut som om det saknas format.

<u>Faktiskt resultat</u>

Format används inte korrekt, bilder saknas.

## Orsak

Sökvägen till bilder och formatmallar är felaktig, antingen på grund av en felaktig bas-URL eller på grund av att serveromskrivningar (CentOS, Ubuntu) inte har konfigurerats korrekt.

Om du vill bekräfta att så är fallet använder du en webbläsarkontroll för att kontrollera sökvägarna till statiska resurser och kontrollera att resurserna finns i filsystemet Adobe Commerce eller Magento Open Source.

Statiska resurser finns under `<magento_root>/pub/static/` , i `frontend` och `adminhtml` kataloger.

## Lösning

Här följer några möjliga lösningar beroende på vilken programvara du använder och orsaken till problemet:

* Om du använder webbservern Apache bör du kontrollera [serveromskrivningar](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/apache.html#apache-help-rewrite) och Adobe Commerce/Magento Open Source-serverns bas-URL och försök igen. Om du har konfigurerat Apache `AllowOverride` -direktivet felaktigt hanteras inte de statiska filerna från rätt plats.
* Om du använder webbservern nginx ska du se till att [konfigurera en virtuell värdfil](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/nginx.html#configure-nginx-ubuntu). Den nya virtuella värdfilen måste uppfylla följande villkor:
   * The `include` -direktivet måste peka på exempelkonfigurationsfilen nginx i installationskatalogen för Adobe Commerce/Magento Open Source. Till exempel:    `include /var/www/html/magento2/nginx.conf.sample;`
   * The `server_name` -direktivet måste matcha den bas-URL som du angav när du installerade Adobe Commerce/Magento Open Source. Till exempel: `server_name 192.186.33.10;`
* Om programmet finns i [produktionsläge](https://devdocs.magento.com/guides/v2.3/config-guide/bootstrap/magento-modes.html#production-mode), prova att distribuera statiska vyfiler med `magento setup:static-content:deploy` -kommando. Mer information om hur du distribuerar statiska filer finns i [Distribuera statiska vyfiler](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-maint.html) i vår dokumentation för utvecklare.
