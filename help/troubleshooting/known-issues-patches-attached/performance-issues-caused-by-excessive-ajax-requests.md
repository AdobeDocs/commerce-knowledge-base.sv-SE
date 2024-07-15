---
title: Prestandaproblem som orsakas av för många Ajax-begäranden
description: Den här artikeln innehåller en patch för de kända prestandaproblemen i Adobe Commerce som orsakas av för många Ajax-begäranden. Problemet har åtgärdats i Adobe Commerce 2.3.4.
exl-id: d9a69406-3970-4556-aa6a-1309b24366d8
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Prestandaproblem som orsakas av för många Ajax-begäranden

Den här artikeln innehåller en patch för de kända prestandaproblemen i Adobe Commerce som orsakas av för många Ajax-begäranden. Problemet har åtgärdats i Adobe Commerce 2.3.4.

## Problem

Adobe Commerce kanske skickar överflödiga [Ajax-begäranden](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) från butiken till servern för att få bannerinformation och kundinformation. Dessa Ajax-förfrågningar har en inverkan på prestandan, särskilt vid stora volymer och hög trafik. Om du inte använder banderollfunktionen bör du [inaktivera Adobe Commerce Banner-modulens utdata](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md) fullständigt och använda korrigeringen för att förbättra hämtningen av kundinformation.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[Hämta MDVA-24597\_EE\_2.2.9\_COMPOSER\_v1.patch](assets/MDVA-24597_EE_2.2.9_COMPOSER_v1.patch.zip)

### Kompatibla Adobe Commerce-versioner

Patchen gäller följande produkter och versioner:

* Adobe Commerce om molninfrastruktur 2.2.9
* Adobe Commerce lokal 2.2.9

Om du har en annan version av Adobe Commerce bör du uppdatera till den senaste 2.3.x-versionen. Om detta inte är ett alternativ för närvarande [kontaktar du Adobe Commerce Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) och begär en patch för din version.

## Så här sätter du på plåstret

Mer information finns i [Använda en dispositionsruta från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## Bifogade filer
