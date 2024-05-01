---
title: .magento.env.yaml ändringar som inte visas i env.php efter distribution
description: Den här artikeln innehåller en lösning på problemet där ändringar i .magento.env.yaml-filen inte återspeglas i app/etc/env.php efter distributionen.
exl-id: 39ea7295-ba5a-40cc-bc68-a5e0b965c1a7
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# .magento.env.yaml ändringar som inte visas i env.php efter distribution

>[!NOTE]
>
>Om du har det här problemet kan du åtgärda det genom att uppgradera till ece-tools 2002.1.5. 2002.1.5 har funktioner för att återställa opcache för varje distribution så att du aldrig behöver ändra inställningen `opcache.enable_cli=1`. Om du inte vill uppgradera måste du utföra de tillfälliga åtgärder som beskrivs nedan i lösningen.

Den här artikeln innehåller en lösning på problemet med att ändringar i `.magento.env.yaml` filen återspeglas inte i `app/etc/env.php` efter driftsättningen.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur (alla [versionerna](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)).

## Problem

Ändringar i `.magento.env.yaml` filen inte påverkar `app/etc/env.php` genereras.

<u>Steg som ska återskapas:</u>

Ändra valfritt värde i `.magento.env.yaml` och skickas till servern där den ska definiera konfigurationen (och distributionsinställningarna) för den utcheckade miljön. Om du vill se steg går du till [Miljövariabler > Distribuera variabler](https://devdocs.magento.com/cloud/env/variables-deploy.html) i vår dokumentation för utvecklare.

<u>Förväntat resultat:</u>

Ändringar i `.magento.env.yaml` filen påverkar `app/etc/env.php` genereras.

<u>Faktiskt resultat:</u>

Ändringarna påverkar inte `app/etc/env.php` variabler efter distributionen.

## Orsak

Problemet kan bero på att värdet på `opcache.enable_cli` -parametern i `php.ini` -fil.

## Lösning

1. Kontrollera att systemet är konfigurerat enligt [Adobe Commerce Performance Best Practices > Programvarurekommendationer](https://devdocs.magento.com/guides/v2.4/performance-best-practices/software.html).
1. Kontrollera om `opcache.enable_cli` direktiv in `php.ini` är inställd på `0` genom att köra: `php -i | grep opcache.enable_cli`
1. Om utdata ser ut som `opcache.enable_cli=1` , redigera `php.ini` i projektets rotkatalog och ändra `opcache.enable_cli=1` till `opcache.enable_cli=0`
1. Distribuera om projektet.

## Relaterad läsning

* [Cloud för Adobe Commerce > Bygg och driftsätt](https://devdocs.magento.com/cloud/project/magento-env-yaml.html).
