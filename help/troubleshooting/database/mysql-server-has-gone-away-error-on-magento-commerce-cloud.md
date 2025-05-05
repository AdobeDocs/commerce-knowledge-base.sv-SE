---
title: MySQL-servern har gått ​ fel på Adobe Commerce i molnet
description: I den här artikeln beskrivs lösningen på problemet där du får felmeddelandet " *SQL-servern har försvunnit*" i filen "cron.log". En rad olika symtom, till exempel problem med bildimportering eller misslyckad distribution, kan uppkomma.
exl-id: 14cb9a6d-6d25-4044-8f52-d65648c03431
feature: Cloud, Paas, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# MySQL-servern har gått &#x200B; fel på Adobe Commerce i molnet

I den här artikeln beskrivs lösningen på problemet där du får felmeddelandet *SQL-servern* i `cron.log`-filen. En rad olika symtom, till exempel problem med bildimportering eller misslyckad distribution, kan uppkomma.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen, alla [versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problem

Du får felmeddelandet *SQL-servern har försvunnit* i filen `cron.log`.

<u>Steg som ska återskapas</u>

Importera filer och utlösa en distribution.

<u>Förväntat resultat</u>

Distributionen lyckades.

<u>Faktiskt resultat</u>

Felmeddelande i `cron.log` :&quot; *SQLSTATE\[HY000\] \[2006\] MySQL-servern har lämnat at/app/AAAAAAAAA/vendor/magento/zendframework1/library/Zend/Db/Adapter/Pdo/Abstract.php:144&quot;*

## Orsak

Värdet `default_socket_timeout` är för lågt. Detta orsakas av inställningen `default_socket_timeout` . Om php inte tar emot något från MySQL-databasen inom den här perioden antas det att den är frånkopplad och att felet uppstår.

## Lösning

1. Kontrollera den aktuella tidsgränsen för `default_socket_timeout` genom att köra i CLI:    ```    php -i |grep default_socket_timeout    ```
1. Beroende på ökningen av timeout-inställningen har variabeln `default_socket_timeout` förväntat längsta möjliga körningstid i filen `/etc/platform/<project_name>/php.ini`. Du bör ange mellan 10 och 15 minuter.
1. Verkställ för GIT och omdistribuera.

## Relaterad läsning

* [Databasöverföringen förlorar anslutningen till MySQL](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md)
* [Bästa databaspraxis för Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=sv-SE)
* [De vanligaste databasproblemen i Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html?lang=sv-SE)
