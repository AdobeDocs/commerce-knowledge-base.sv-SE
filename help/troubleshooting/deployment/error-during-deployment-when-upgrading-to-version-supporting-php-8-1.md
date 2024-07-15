---
title: Ett fel uppstod vid distributionen när versionen som stöder PHP 8.1 uppgraderades
description: Den här artikeln innehåller en lösning på det fel som inträffar under distributionen vid uppgradering till en version som stöder PHP 8.1.
exl-id: bdc4a355-4f2b-49a7-9c5d-63c950f7ca30
feature: Deploy, Observability
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Ett fel uppstod vid distributionen när versionen som stöder PHP 8.1 uppgraderades

Den här artikeln innehåller en lösning på det fel som inträffar under distributionen vid uppgradering till en version som stöder PHP 8.1.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.4.4 och senare

* Tillägg eller teknik (snabbt, New Relic osv.) version PHP 8.1

## Problem

Följande fel inträffar under distributionen vid uppgradering till en version som stöder PHP 8.1.

```PHP
{{E: Error parsing configuration files:

applications: Uncaught exception: The "json" extension is not supported for php:8.1
at <script>:109:12
throw("The \"" + unsupported_extensions[0] + "\" extension is not supported for " + service.type);
^
E: Error: Invalid configuration files, aborting build}}
```

## Orsak

PHP 8.1 har redan stöd för JSON och kräver inte att tillägget installeras separat.

## Lösning

Ta bort JSON från avsnittet **Runtime** > **Extensions** i `.magento.app.yaml` och distribuera om.

## Relaterad läsning

[PHP-programmet](https://devdocs.magento.com/cloud/project/magento-app-php-application.html) i utvecklardokumentationen.
