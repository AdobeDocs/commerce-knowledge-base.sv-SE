---
title: Vanliga PHP-allvarliga fel och lösningar
description: I den här artikeln listas några vanliga snabba PHP Fatal Error-exempel som du kan hitta när du tittar igenom dina Adobe Commerce-loggar och lösningar på problem som de ger upphov till.
exl-id: 3e42d38f-97bc-4d38-8e36-23b1453f81d9
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Vanliga PHP-allvarliga fel och lösningar

I den här artikeln listas några vanliga snabba PHP Fatal Error-exempel som du kan hitta när du tittar igenom dina Adobe Commerce-loggar och lösningar på problem som de ger upphov till.

## Exempel

Allvarligt fel i PHP för *: Maximal körningstid på 60 sekunder har överskridits i...*

## Lösning

Du kan uppdatera den maximala körningstiden genom att ange ett anpassat `max_execution_time`-värde i `php.ini`-filen och omdistribuera den.

Exempel:

`max_execution_time = 120`

Läs artikeln [Anpassa inställningar för php.ini](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html).

## Exempel

Allvarligt fel i PHP för *: Tillåten minnesstorlek på 792723456 byte är slut* (det är bara en exempelbytestorlek.)

## Lösning

Anpassa dina `php.ini`-inställningar. Läs den här [Anpassa php.ini-inställningsartikeln](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html).

## Exempel

PHP-varning för *: Okänd: det gick inte att öppna dataströmmen: Det finns ingen sådan fil eller katalog*

## Lösning

Se till att du inte tar bort Windows-formatets slut i filen `php.ini`. I Windows avslutas radslut med en kombination av vagnretur (ASCII 0x0d eller \r) och en radmatning (\n), som även kallas CR/LF.

## Exempel

*&#39;Allvarligt PHP-fel: Ohanterad PDOException: SQLSTATE\[HY000\] \[1040\] För många anslutningar i&#39;*

## Lösning

MySQL-miljön har slut på diskutrymme. Ange mer diskutrymme för MySQL-miljön.

## Exempel

Allvarligt fel i PHP för *: Ohanterad TypeError: Returvärdet för Magento*

## Lösning

Kontrollera katalogen `<root>/tmp` eftersom den förmodligen är full. Om den är full anger du mer utrymme i katalogen. Detta kan innebära att du helt enkelt flyttar filer till en annan katalog eller tar bort dem.

## Relaterad läsning

I vår utvecklardokumentation:

* [PHP-inställningsfel](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html)
* [Nödvändiga PHP-inställningar](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html)
* [Redis-verifiering](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify)
* [Konfigurera Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html)
* [PHP-minnesbegränsningsfel](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html#trouble-php-memory)
* [Lösningar på vanliga problem - minnesbegränsning](https://devdocs.magento.com/guides/v2.3/test/unit/unit_test_execution_cli.html#solutions-to-common-problems)
