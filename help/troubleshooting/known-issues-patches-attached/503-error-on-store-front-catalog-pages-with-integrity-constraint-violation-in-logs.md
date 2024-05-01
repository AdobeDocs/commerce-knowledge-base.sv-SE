---
title: 503-fel vid lagring av frontkatalogsidor med överträdelse av integritetsbegränsning i loggar
description: Den här artikeln innehåller en patch för det kända problemet med Adobe Commerce i molninfrastruktur 2.2.0 som handlar om att lagra katalogsidor som inte är tillgängliga.
exl-id: ad363744-756a-48b9-ae11-58642e0ca6a4
feature: Catalog Management, Logs
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# 503-fel vid lagring av frontkatalogsidor med överträdelse av integritetsbegränsning i loggar

>[!NOTE]
>
>Den här artikeln innehåller en patch som en tillfällig lösning, men problemet har åtgärdats permanent i Adobe Commerce i molninfrastrukturversionen v2.3.3 och du bör uppgradera till v2.3.3. Följ stegen i [Uppgradera Adobe Commerce](https://devdocs.magento.com/cloud/project/project-upgrade.html) i vår dokumentation för utvecklare.

I den här artikeln finns en patch för det kända problemet med Adobe Commerce i molninfrastruktur 2.2.0 som handlar om att lagra katalogsidor som inte är tillgängliga. Felmeddelandet liknar följande i loggen: *Överträdelse av integritetsbegränsning: 1062 Dubblettposten %entry% för nyckeln PRIMARY, frågan var: INSERT INTO \`search\_tmp\_%number%*.

## Problem

Butikens katalogsidor blir oväntat oåtkomliga. Felloggen innehåller en felbeskrivning som liknar följande: *Överträdelse av integritetsbegränsning: 1062 Dubblettposten %entry% för nyckeln PRIMARY, frågan var: INSERT INTO \`search\_tmp\_%number%*.

Problemet är relaterat till sökning och orsakas av att det finns ett inaktuellt index tillsammans med det nya efter omindexering.

## Lösning

För att åtgärda problemet måste du ta bort inaktuella index från Elasticsearch och tillämpa korrigeringen för att förhindra att de visas.

Använd följande kommando för att lista alla index:

<pre>curl -X GET %elasticsearch_domain%:%elasticsearch_port%/_cat/indices</pre>

Om du vill ta bort inaktuella index söker du efter dem i databasen och använder följande kommando:

```bash
curl -X DELETE %elasticsearch_domain%:%elasticsearch_port%/%product_id%_v%outdated_version%
```

Exempel:

```bash
curl -X DELETE 127.0.0.1:9200/magento2_product_8_v332
```

## Lappa

Patcherna är kopplade till den här artikeln. Om du vill hämta en patch rullar du nedåt till slutet av artikeln och klickar på önskat filnamn, eller klickar på någon av följande länkar:

[Hämta MDVA-9590\_EE\_2.2.0\_COMPOSER\_v2.patch](assets/MDVA-9590_EE_2.2.0_COMPOSER_v2.patch.zip)

[Ladda ned MDVA-13203\_EE\_2.2.4\_V1\_COMPOSER.patch](assets/MDVA-13203_EE_2.2.4_V1_COMPOSER.patch.zip)

## Kompatibla Adobe Commerce-versioner

Patcharna skapades för följande utgåvor och versioner:

* Adobe Commerce om molninfrastruktur 2.2.0 (`MDVA-9590_EE_2.2.0_COMPOSER_v2.patch`)
* Adobe Commerce om molninfrastruktur 2.2.4 (`MDVA-13203_EE_2.2.4_V1_COMPOSER.patch`)

The `MDVA-9590_EE_2.2.0_COMPOSER_v2` patch är också kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce om molninfrastruktur 2.0.X, 2.1.X, 2.2.X och 2.3.0 - 2.3.3
* Adobe Commerce lokalt 2.0.X, 2.1.X, 2.2.X och 2.3.0 - 2.3.3

The `MDVA-13203_EE_2.2.4_V1_COMPOSER` patch är också kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce om molninfrastruktur 2.0.X, 2.1.X, 2.2.X och 2.3.0 - 2.3.3
* Adobe Commerce lokalt 2.0.X, 2.1.X, 2.2.X och 2.3.0 - 2.3.3

## Så här sätter du på plåstret

Instruktioner finns i [Använda en kompositkorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.

## Användbara länkar

* [Loggfilsplats för Adobe Commerce på arkitekturen för molninfrastrukturen Starter-planen](/help/how-to/general/log-locations-directories-for-starter-plan.md) i vår kunskapsbas för support.
* [Loggfilsplats för Adobe Commerce på Cloud Infrastructure Pros planarkitektur](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) i vår kunskapsbas för support.
* [Loggfilsplats för Adobe Commerce](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html) i vår dokumentation för utvecklare.

## Bifogade filer
