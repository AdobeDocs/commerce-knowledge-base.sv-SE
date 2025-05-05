---
title: Efter installationen läses inte bilder och formatmallar in; endast textvisning, ingen grafik
description: I den här artikeln beskrivs möjliga orsaker och lösningar till problemet där formatmallar och bilder inte läses in efter installation av Adobe Commerce.
exl-id: f33cee89-b416-4d63-8cc5-9cc57618ce92
feature: Install, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Statiska resurser finns under `<magento_root>/pub/static/`, i katalogerna `frontend` och `adminhtml`.

## Lösning

Här följer några möjliga lösningar beroende på vilken programvara du använder och orsaken till problemet:

* Om du använder webbservern Apache kontrollerar du att inställningen [server skriver om](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/prerequisites/web-server/apache#apache-rewrites-and-htaccess) och Adobe Commerce/Magento Open Source-serverns bas-URL och försöker igen. Om du har konfigurerat Apache `AllowOverride`-direktivet på ett felaktigt sätt kommer de statiska filerna inte att hanteras från rätt plats.
* Om du använder webbservern nginx måste du [konfigurera en virtuell värdfil](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/prerequisites/web-server/nginx). Den nya virtuella värdfilen måste uppfylla följande villkor:
   * Direktivet `include` måste peka på exempelkonfigurationsfilen nginx i installationskatalogen för Adobe Commerce/Magento Open Source. Till exempel:    `include /var/www/html/magento2/nginx.conf.sample;`
   * Direktivet `server_name` måste matcha den bas-URL som du angav när du installerade Adobe Commerce/Magento Open Source. Till exempel: `server_name 192.186.33.10;`
* Om programmet är i [produktionsläge](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/setup/application-modes#production-mode) kan du försöka distribuera statiska vyfiler med kommandot `magento setup:static-content:deploy`. Mer information om hur du distribuerar statiska filer finns i [Distribuera statiska vyfiler](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i utvecklardokumentationen.
