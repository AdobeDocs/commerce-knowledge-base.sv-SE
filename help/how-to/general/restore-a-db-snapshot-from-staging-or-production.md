---
title: Återställ en DB-ögonblicksbild från mellanlagring eller produktion
description: I den här artikeln beskrivs hur du återställer en DB-ögonblicksbild från Staging eller Production på Adobe Commerce i molninfrastrukturen.
exl-id: 1026a1c9-0ca0-4823-8c07-ec4ff532606a
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Återställ en DB-ögonblicksbild från [!DNL Staging] eller [!DNL Production]

I den här artikeln visas hur du återställer en DB [!DNL snapshot] från [!DNL Staging] eller [!DNL Production] på Adobe Commerce i molnPro-infrastrukturen.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur, [alla versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Välj det alternativ som passar bäst:

* [Metod 1: Överför databasen [!DNL dump] till den lokala datorn och importera den](#meth2).
* [Metod 2: Importera databasen [!DNL dump] direkt från servern](#meth3).

## Metod 1: Överför databasen [!DNL dump] till den lokala datorn och importera den {#meth2}

Stegen är:

1. Använd [!DNL SFTP] och navigera till den plats där databasen [!DNL snapshot] har placerats, vanligtvis på den första servern/noden i [!DNL cluster] (till exempel: `/mnt/recovery-<recovery_id>`). Obs! Om ditt projekt är Azure-baserat, d.v.s. din projekt-URL ser ut ungefär som https://us-a1.magento.cloud/projects/&lt;Cluster_id>, placeras ögonblicksbilden i `/mnt/shared/<cluster ID>/all-databases.sql.gz` eller `/mnt/shared/<cluster ID_stg>/all-databases.sql.gz` i stället.

   Obs! Formatet på ögonblicksbilden i Azure-projekt kommer att vara annorlunda och innehåller andra databaser som inte kan importeras. Innan du importerar ögonblicksbilden kommer du     måste vidta ytterligare åtgärder för att extrahera lämplig databas innan dumpen importeras.

   För produktion:

   ```sql
   cd /mnt/shared/<cluster ID/
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID>.sql 
   sed -n '/^-- Current Database: `<cluster ID>`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID>.sql gzip <cluster ID>.sql
   zcat <cluster ID>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

   För mellanlagring:

   ```sql
   cd /mnt/shared/<cluster ID/ | cd /mnt/shared/<cluster ID_stg>
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID_stg>.sql
   sed -n '/^-- Current Database: `wyf2o4zlrljjs`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID_stg>.sql 
   gzip <cluster ID_stg>.sql  
   zcat <cluster ID_stg>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

1. Kopiera databasen [!DNL dump file] (till exempel: `<cluster ID>.sql.gz` för [!DNL Production] eller `<cluster ID_stg>.sql.gz` för [!DNL Staging]) till den lokala datorn.
1. Kontrollera att du har konfigurerat [!DNL SSH tunnel] för fjärranslutning till databasen: [[!DNL SSH]  och [!DNL sFTP]: [!DNL SSH tunneling]](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#env-start-tunn) i utvecklardokumentationen.
1. Anslut till databasen.

   ```sql
   mysql -h <db-host> -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] databasen. Ange:[!DNL MariaDB]

   (för [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (för [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. Ange följande kommando för att importera [!DNL snapshot]:

   (för [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

   (för [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

## Metod 2: Importera databasen [!DNL dump] direkt från servern {#meth3}

Stegen är:

1. Navigera till platsen där databasen [!DNL snapshot] har placerats, vanligtvis på den första servern/noden i [!DNL cluster] (till exempel: `/mnt/recovery-<recovery_id>`).
1. Om du vill [!DNL drop] och återskapa molndatabasen ansluter du först till databasen:

   ```sql
   mysql -h 127.0.0.1 -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] databasen. Ange:[!DNL MariaDB]

   (för [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (för [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. Ange följande kommando för att importera [!DNL snapshot]:

   (Vid import av säkerhetskopiering av databas från [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Vid import av säkerhetskopiering av databas från [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (För import av en säkerhetskopiering av en databas från någon annan miljö)

   ```sql
   zcat <database-backup-name>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (För import av en säkerhetskopiering av en databas från någon annan miljö)

   ```sql
   zcat <database-backup-name>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

## Relaterad läsning

I vår utvecklardokumentation:

* [Importera kod: Importera databasen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production)
* [[!DNL Snapshots] och [!DNL backup] hantering: [!DNL Dump] din databas](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)
