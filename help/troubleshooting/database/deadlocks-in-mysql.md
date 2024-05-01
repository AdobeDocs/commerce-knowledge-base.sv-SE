---
title: Deadlocks in MySQL
description: Den här artikeln handlar om dödlägen i MySQL för att hjälpa till att identifiera och lösa dem om de orsakar problem med en webbplats, fast databasimport eller andra Adobe Commerce-problem.
exl-id: 529d1c0b-77f3-4604-9878-e7ea2c9c3640
feature: Best Practices, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Deadlocks in MySQL

Den här artikeln handlar om dödlägen i MySQL för att hjälpa till att identifiera och lösa dem om de orsakar problem med en webbplats, fast databasimport eller andra Adobe Commerce-problem.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.2.x och 2.3.x
* Adobe Commerce i molninfrastruktur 2.2.x och 2.3.x

## Problem

Deadlocks i MySQL inträffar när två eller flera transaktioner håller ihop och begär lås. Deadlocks som finns tyder inte alltid på ett problem, utan är ofta ett symtom på något annat MySQL- eller Adobe Commerce-problem som har inträffat.

Programmet, distributionen eller MySQL-loggarna anger ofta en *&quot;deadlock&quot;* fel eller fel *&quot;Det gick inte att låsa vid försök att låsa. Försök starta om transaktionen.&quot;*

## Orsak

Deadlocks kan ha flera orsaker, men det vanligaste är om du utför någon interaktion (webbplats/processer/cron-jobb/andra användare/MySQL-underhåll/MySQL-importer) samtidigt som du utför DML-/DDL-frågor.

Det är till exempel en bra rutin att undvika en fastsatt import av MySQL-databas genom att först försätta platsen i underhållsläge för att undvika att SQL-begäranden skickas till databasen som kan orsaka lås och en fast databasimport.

## Lösning

1. Kontrollera programmet, distributionen eller MySQL-loggarna för att se om det finns några dödlåsningsfel:
   * [Loggplatser för Adobe Commerce och Magento Open Source](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/enable-logging.html)
   * [Adobe Commerce på platser för molninfrastrukturloggar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)
1. Kontrollera din MySQL-processlista för att köra processer med kommandot `mysql -e 'show full processlist';`
1. Om du använder Adobe Commerce i molninfrastruktur kontrollerar du att MySQL-slav är aktiverat. Läs den här artikeln: [Distribuera variabler (MYSQL\_USE\_SLAVE\_CONNECTION)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection).
1. Beroende på vilka fel som har uppstått kan lösningen vara egen eller så måste du inkludera din användbara logginformation om du behöver öppna en [Supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Relaterad läsning

* [Minimera och hantera lås](https://dev.mysql.com/doc/refman/5.7/en/innodb-deadlocks-handling.html)
* [Indexeraroptimering - indexerartabellväxling](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/)
* [Massåtgärder - konsumera meddelanden](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

>[!NOTE]
>
>Vi är medvetna om att den här artikeln fortfarande kan innehålla programtermer som är branschstandard och som vissa kan finna rasistiska, sexistiska eller förtryckande och som kan få läsaren att känna sig sårad, traumatiserad eller ovälkommen. Adobe arbetar med att ta bort dessa villkor från vår kod, dokumentation och användarupplevelse.
