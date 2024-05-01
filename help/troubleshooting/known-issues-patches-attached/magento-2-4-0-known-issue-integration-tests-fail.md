---
title: "Problem med Adobe Commerce 2.4.0: integrationstester misslyckas"
description: Den här artikeln innehåller en patch för Adobe Commerce 2.4.0-problemet där integreringstester misslyckas eftersom deklarationen av "Dotdigitalgroup\Email\Test\Integration\Model\Sync\Importer\ImporterFailedTest::setUp()" inte är kompatibel med PHPUnit 9 som används för 2.4.0.
exl-id: 8e0ca2da-81d9-4561-a009-593240f46e41
feature: Integration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Känt fel i Adobe Commerce 2.4.0: integrationstester misslyckas

Den här artikeln innehåller en patch för Adobe Commerce 2.4.0-problemet där integreringstester misslyckas på grund av deklarationen av `Dotdigitalgroup\Email\Test\Integration\Model\Sync\Importer\ImporterFailedTest::setUp()` är inte kompatibelt med PHPUnit 9 som används för 2.4.0.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.4.0
* Adobe Commerce lokal 2.4.0

## Problem

<u>Steg som ska återskapas</u>

Kör integrationstester för 2.4.0.

<u>Förväntat resultat</u>

Testerna går.

<u>Faktiskt resultat</u>

*Allvarligt PHP-fel: Deklarationen av Dotdigitalgroup\\Email\\Test\\Integration\\Model\\Sync\\Importer\\ImporterFailedTest::setUp() måste vara kompatibel med PHPUnit\\Framework\\TestCase::setUp(): void i /var/www/vendor/dotmailer/dotmailer-magento2-extension/Test/Integration/Model/Sync/Importer/ImporterFailedTest.php på rad 36*

## Lösning

Använd den patch som finns i den här artikeln.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[BUNDLE-2684-composer.patch](assets/BUNDLE-2684-composer.patch.zip)

### Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce om molninfrastruktur 2.4.0
* Adobe Commerce lokal 2.4.0

## Så här sätter du på plåstret

Se [Använda en kompositkorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support för instruktioner.

## Bifogade filer
