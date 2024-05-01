---
title: Nyckelprocedurer för Github-token och Composer
description: Den här artikeln innehåller lösningar på problem med misslyckade distributioner relaterade till misslyckade Github-tokenfel orsakade av inaktuella Composer-nycklar.
exl-id: 202cb936-f9ba-49ea-bf0a-6e6994d2337a
feature: Identity Management
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Nyckelprocedurer för Github-token och Composer

Den här artikeln innehåller lösningar på problem med misslyckade distributioner relaterade till misslyckade Github-tokenfel orsakade av inaktuella Composer-nycklar.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur, [alla versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Composer version 1.10.20 och tidigare

>[!NOTE]
>
>Adobe Commerce lokala handlare bör kontrollera med sin värdleverantör att de använder Composer version 1.10.21 eller senare på grund av ändringar i tokenformatet som introducerats av Git.

## Problem

Distributioner misslyckas och distributionsloggarna innehåller information som liknar följande:

*Allvarligt fel: Uncaught UnexpectedValueException: Din github-auth-token för github.com innehåller ogiltiga tecken: &quot;ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx&quot; i /app/vendor/composer/composer/src/Composer/IO/BaseIO.php:129*

## Orsak

Inaktuella dispositionsnycklar orsakar fel på Github-token som resulterar i misslyckade distributioner.

## Lösning

Du löser problemet genom att uppdatera din Composer-version till 1.10.22:

1. I din lokala miljö kan du köra `composer require “composer/composer”:”>1.10.21`.
1. Detta lägger till kravet för den versionen av Composer-paketet. Kontrollera låsfilen - `composer/composer` version måste vara 1.0.22 eller senare.
1. Verkställ `composer.json` och `composer.lock` och driva en driftsättning.

Om den här metoden inte fungerar, [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Relaterad läsning

* [Github Blog: Bakom GitHub:s nya autentiseringstokenformat](https://github.blog/2021-04-05-behind-githubs-new-authentication-token-formats/)
* [InfoQ.com: GitHub Changes Token Format to Improved Identifiability, Secret Scanning, and Entropy](https://www.infoq.com/news/2021/04/github-new-token-format/)
