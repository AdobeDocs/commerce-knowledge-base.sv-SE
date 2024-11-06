---
title: Kontrollera långsamma frågor och processer MySQL
description: I den här artikeln beskrivs några vanliga MySQL-problem (långsamma frågor, processer som tar för lång tid) som kan påverka en handlares webbplats negativt och de lösningar som de anger.
exl-id: cae02e4f-d8cb-4074-abac-24ead22bdc07
feature: Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Kontrollera långsamma frågor och processer MySQL

I den här artikeln beskrivs några vanliga MySQL-problem (långsamma frågor, processer som tar för lång tid) som kan påverka en handlares webbplats negativt och de lösningar som de anger.

## Kontrollerar &quot;långsamma frågor&quot; i MySQL

### Beskrivning

Om du har råkat ut för ett driftavbrott som kan ha orsakats av en överlagrad databas kan du använda de här stegen för att kontrollera databasens långsamma frågelogg.

### Analysera frågor med hjälp av kommandoraden i MySQL (Adobe Commerce Cloud/lokal/Magento Open Source)

1. Logga in på din MySQL-kommandorad (Adobe Commerce lokalt/Magento Open Source) eller på din molnserver från kommandoraden (Adobe Commerce i molninfrastruktur).
1. Granska den långsamma frågeloggen för frågor som är längre än 50 sekunder:

   ```bash
   grep 'Query_time: [5-9][0-9]\|Query_time: [0-9][0-9][0-9]' /var/log/mysql/mysql-slow.log -A 3
   ```

1. Gå till <https://www.unixtimestamp.com/> (eller en liknande Unix-tidsstämpelkonverterare) och infoga tidsstämpeln för när den långsamma frågan kördes.
1. Om tiden motsvarar eventuella driftavbrott kan det bero på en överlagrad databas. Kontrollera vilka inläsningar som fanns i databasen vid den tidpunkten. Exempel på sådana laster kan vara:

* Cron-processer
* Trafik (bilar eller människor)
* Importera/exportera skript
* Skapa dumpar


### Analysera frågor med [!DNL Percona Toolkit] (Adobe Commerce Pro: endast molnarkitekturen)

Om ditt Adobe Commerce-projekt har distribuerats på Pro-arkitekturen kan du använda [!DNL Percona Toolkit] för att analysera frågor.

1. Kör kommandot `pt-query-digest --type=slowlog` mot långsamma MySQL-frågeloggar.
   * Information om var de långsamma frågeloggarna finns i **[[!UICONTROL Log locations > Service Logs]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)** i utvecklardokumentationen.
   * Se dokumentationen för [[!DNL Percona Toolkit] > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest).
1. Beroende på vilka problem som hittas kan du åtgärda frågan så att den körs snabbare.

## Kontrollerar MySQL-processlista

### Beskrivning

Detta hjälper till att identifiera om MySQL-servern är aktiv och att det inte finns några fastsatta frågor.

### Steg

1. Logga in på din MySQL-kommandorad (Adobe Commerce lokalt/Magento Open Source) eller på din molnserver från kommandoraden (Adobe Commerce i molninfrastruktur).
1. Logga in på MySQL med kodblocket nedan. Detta automatiserar inloggningsprocessen.

   ```MySQL
   `export DB_NAME=$(grep [\']db[\'] -A 20 app/etc/env.php | grep dbname | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_HOST=$(grep [\']db[\'] -A 20 app/etc/env.php | grep host | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export DB_USER=$(grep [\']db[\'] -A 20 app/etc/env.php | grep username | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_PWD=$(grep [\']db[\'] -A 20 app/etc/env.php | grep password | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/[']$//" | sed "s/['][,]//");    mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;`
   ```

1. Om du får tillbaka ett fel eller om det tar mer än 30 sekunder att svara kontaktar du supporten för att kontrollera MySQL-servern.
1. Titta på exempelutdata.

1. Här följer några exempel på utdata:

   ```MySQL
   `$ mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;'    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | Id        | User          | Host               | db            | Command | Time | State          | Info                                                                                                 | Progress |    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | 123456789 | abcdefghijklm | 192.168.7.10:12345 | abcdefghijklm | Query   |    0 | Writing to net | SELECT `magento_versionscms_hierarchy_node`.*, `page_table`.`title` AS `page_title`, `page_table`.`i |    0.000 |    | 123456788 | abcdefghijklm | 192.168.7.10:12344 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456777 | abcdefghijklm | 192.168.7.10:12333 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456666 | abcdefghijklm | 192.168.5.8:12222  | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |`
   ```

1. Kontrollera kolumnen&quot;Tid&quot; för en tid som är längre än 1 800 sekunder, vilket anger en process som kan ta för lång tid att slutföra. Observera status för processerna i kolumnen Läge.
1. Granska frågorna och stäng dem eventuellt om de inte förväntas köras under den tiden. Det är möjligt att de frågor som körs så länge kan förväntas.


## Relaterad läsning

* [MySQL - visa processlistsyntax](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) i dev.mysql.com.
* [MySQL Kill Syntax](https://dev.mysql.com/doc/refman/8.0/en/kill.html) i dev.mysql.com.
* [Säkerhet, prestanda och datahantering](https://developer.adobe.com/commerce/php/best-practices/extensions/security/) i utvecklardokumentationen.
* [MySQL-hjälp](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql) i utvecklardokumentationen.
