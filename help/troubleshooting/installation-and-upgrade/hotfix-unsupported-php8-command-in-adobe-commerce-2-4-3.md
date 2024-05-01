---
title: Adobe Commerce upgrade 2.4.3, 2.3.7-p1 PHP Fatal error Hotfix
description: "Den här artikeln innehåller en fix för när handlare försöker uppgradera till Adobe Commerce (alla distributionsmetoder) eller Magento Open Source 2.4.3 eller 2.3.7-p1 som ser följande fel:"
exl-id: 1c472214-8387-403e-b2d2-d3f3c9e1da6a
feature: Install, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Adobe Commerce upgrade 2.4.3, 2.3.7-p1 PHP Fatal error Hotfix

I den här artikeln finns en korrigering för när handlare försöker uppgradera till Adobe Commerce (alla distributionsmetoder) eller Magento Open Source 2.4.3 eller 2.3.7-p1 som ser följande fel:

*Allvarligt PHP-fel: Ohanterat fel: Anrop till den odefinierade funktionen Magento\Framework\Filesystem\Directory\str_contains() i &lt;..>/magento/vendor/magento/framework/Filesystem/Directory/DenyListPathValidator.php:74*

Problemet kommer att åtgärdas i version 2.4.4, 2.4.3-p1 och 2.3.7-p2.

## Berörda versioner och produkter

* Adobe Commerce (alla distributionsmetoder) vid uppgradering till 2.3.7-p1 eller 2.4.3.
* Magento Open Source vid uppgradering till 2.3.7-p1 eller 2.4.3.

## Problem

Problemet orsakas av de nya versionerna av Adobe Commerce 2.4.3 och 2.3.7-p1 som endast använder funktionen PHP 8 `str_contains`. Adobe Commerce 2.4.3 och 2.3.7-p1 är bara kompatibla med PHP 7.4, så den här funktionen kan inte användas.

<u>Steg som ska återskapas</u> :

Försök att uppgradera till Adobe Commerce 2.4.3 eller 2.3.7-p1.

<u>Förväntat resultat:</u>

Uppgraderingen lyckades.

<u>Faktiskt resultat:</u>

Allvarligt PHP-fel.

## Lösning

Du kan lösa det genom att köra följande kommando i CLI/Terminal: `composer require symfony/polyfill-php80` från rotmappen i Magento eller installera en kompositörkorrigering.

För att åtgärda problemet i 2.4.3 bör Adobe Commerce (alla distributionsmetoder) och Magento Open Source handlare tillämpa en patch:

[AC-384_Fix_Incompatible_PHP_Method__2.4.3_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.4.3_ce.patch.zip)

För att åtgärda problemet med 2.3.7-p1 bör Adobe Commerce (alla distributionsmetoder) och Magento Open Source handlare tillämpa en patch:

[AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch.zip)

## Så här använder du patchen

Se [Använda en kompositkorrigering från Magento](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) för instruktioner.

## Relaterad läsning

GitHub [PHP 8-kommandot stöds inte i Magento 2.4.3 EE #33680](https://github.com/magento/magento2/issues/33680)
