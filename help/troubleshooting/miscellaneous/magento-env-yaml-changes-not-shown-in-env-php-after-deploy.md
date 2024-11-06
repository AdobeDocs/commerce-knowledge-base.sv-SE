---
title: .magento.env.yaml ändringar som inte visas i env.php efter distribution
description: Den här artikeln innehåller en lösning på problemet där ändringar i .magento.env.yaml-filen inte återspeglas i app/etc/env.php efter distributionen.
exl-id: 39ea7295-ba5a-40cc-bc68-a5e0b965c1a7
feature: Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# .magento.env.yaml ändringar som inte visas i env.php efter distribution

>[!NOTE]
>
>Om du har det här problemet kan du åtgärda det genom att uppgradera till ece-tools 2002.1.5. 2002.1.5 har funktioner för att återställa opcache för varje distribution så att du aldrig behöver ändra inställningen `opcache.enable_cli=1`. Om du inte vill uppgradera måste du utföra de tillfälliga åtgärder som beskrivs nedan i lösningen.

Den här artikeln innehåller en lösning på problemet där ändringar i filen `.magento.env.yaml` inte återspeglas i `app/etc/env.php` efter distributionen.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur (alla [versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)).

## Problem

Ändringar som görs i filen `.magento.env.yaml` påverkar inte `app/etc/env.php` som genereras.

<u>Steg att återskapa:</u>

Ändra ett värde i `.magento.env.yaml` och skicka till servern, där konfigurationen (och distributionsinställningarna) för den utcheckade miljön ska definieras. Stegen finns i [Miljövariabler > Distribuera variabler](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy) i utvecklardokumentationen.

<u>Förväntat resultat:</u>

Ändringar som görs i filen `.magento.env.yaml` påverkar `app/etc/env.php` som genereras.

<u>Faktiskt resultat:</u>

Ändringarna påverkar inte `app/etc/env.php`-variablerna efter distributionen.

## Orsak

Problemet kan bero på det felaktiga värdet för parametern `opcache.enable_cli` i filen `php.ini`.

## Lösning

1. Kontrollera att systemet är konfigurerat enligt [Adobe Commerce Performance Best Practices > Software recommendations](https://experienceleague.adobe.com/en/docs/commerce-operations/performance-best-practices/software).
1. Kontrollera om direktivet `opcache.enable_cli` i `php.ini` är inställt på `0` genom att köra: `php -i | grep opcache.enable_cli`
1. Om utdata ser ut som `opcache.enable_cli=1` redigerar du filen `php.ini` i projektets rotkatalog och ändrar `opcache.enable_cli=1` till `opcache.enable_cli=0`
1. Distribuera om projektet.

## Relaterad läsning

* [Cloud för Adobe Commerce > Skapa och distribuera](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml).
