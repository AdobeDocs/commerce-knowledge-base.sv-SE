---
title: Skapa databasdump på Adobe Commerce i molninfrastrukturen
description: I den här artikeln beskrivs de möjliga (och rekommenderade) sätten att skapa en databasdump (DB) på Adobe Commerce i molninfrastrukturen.
exl-id: 4a2e54ac-8d65-4e51-8337-08f9748dc6c0
feature: Cloud
source-git-commit: 96b145a1f76c296907da96fd97c7a8f7778463f8
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Skapa databasdump på Adobe Commerce i molninfrastrukturen

I den här artikeln beskrivs de möjliga (och rekommenderade) sätten att skapa en databasdump (DB) på Adobe Commerce i molninfrastrukturen.

Du behöver bara använda en variant (alternativ) för att dumpa din databas. Dessa alternativ gäller alla miljötyper (integrering, mellanlagring, produktion) och alla planer (Adobe Commerce på molninfrastrukturen Starter-planarkitekturen och Adobe Commerce på molninfrastrukturproffsens planarkitektur).

## Krav: SSH i din miljö

Om du vill dumpa din databas på Adobe Commerce i molninfrastruktur med någon variant som beskrivs i den här artikeln måste du först [SSH till din miljö](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).

>[!WARNING]
>
>Oavsett om du väljer Alternativ 1 eller Alternativ 2 ska du köra kommandot under tider med låg belastning mot en sekundär databasnod.

## Alternativ 1: db-dump (**ece-tools; rekommenderas**)

Du kan dumpa din databas med kommandot [ECE-Tools](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html):

```php
vendor/bin/ece-tools db-dump
```

Detta är det rekommenderade och säkraste alternativet.

Se [Dumpa din databas (ECE-verktyg)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/database-dump.html) i vår Commerce on Cloud Infrastructure Guide.

## Alternativ 2: mariadb-dump (eller mysqldump för äldre versioner)

+++<b>För nyare MariaDB-versioner (11.x och senare)</b>

Från och med MariaDB 11.0.1 är symlänken `mysqldump` föråldrad. Du rekommenderas att använda `mariadb-dump` i stället.

Mer information finns i [mariadb-dump-klientverktyget](https://mariadb.com/docs/server/clients-and-utilities/backup-restore-and-import-clients/mariadb-dump).

+++

+++<b>För äldre MariaDB-versioner</b> 

Om du använder en äldre MariaDB-version där `mariadb-dump` inte är tillgänglig kan du dumpa din databas med hjälp av det inbyggda MySQL `mysqldump` -kommandot.

>[!WARNING]
>
>Kör inte det här kommandot mot databaskluster. Klustret skiljer inte åt om det körs mot den primära databasen eller mot en sekundär. Om klustret kör det här kommandot mot det primära, kommer databasen inte att kunna köra skrivningar förrän dumpningen är klar och kan påverka prestanda och webbplatsens stabilitet.

Hela kommandot kan se ut så här:

```sql
mysqldump -h <host> -u <username> -p <password> --single-transaction <db_name> | gzip > /tmp/<dump_name>.sql.gz
```

Säkerhetskopian av databasen som skapades genom att köra kommandot `mysqldump` och sparades i `\tmp` bör flyttas från den här platsen. Det ska inte ta upp lagringsutrymme i `\tmp` (vilket kan leda till problem).

+++

Du kan anropa miljövariabeln `MAGENTO_CLOUD_RELATIONSHIPS` för att få dina DB-autentiseringsuppgifter (värd, användarnamn och lösenord):

```
echo $MAGENTO_CLOUD_RELATIONSHIPS |base64 --d |json_pp
```

**Relaterad dokumentation:**

* [mysqldump - Ett program för säkerhetskopiering av databas](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) i officiell MySQL-dokumentation.
* [Molnspecifika variabler](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html) (se `MAGENTO_CLOUD_RELATIONSHIPS`) i vår Commerce on Cloud Infrastructure Guide.
