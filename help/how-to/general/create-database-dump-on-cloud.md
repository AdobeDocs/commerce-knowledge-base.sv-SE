---
title: Skapa databasdump på Adobe Commerce i molninfrastrukturen
description: I den här artikeln beskrivs de möjliga (och rekommenderade) sätten att skapa en databasdump (DB) på Adobe Commerce i molninfrastrukturen.
exl-id: 4a2e54ac-8d65-4e51-8337-08f9748dc6c0
feature: Cloud
source-git-commit: 0948b2a94ee4f2a355e7c024a09929f0ad223783
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Skapa databasdump på Adobe Commerce i molninfrastrukturen

I den här artikeln beskrivs de möjliga (och rekommenderade) sätten att skapa en databasdump (DB) på Adobe Commerce i molninfrastrukturen.

Du behöver bara använda en variant (alternativ) för att dumpa din databas. Dessa alternativ gäller alla miljötyper (integrering, mellanlagring, produktion) och alla planer (Adobe Commerce på molninfrastrukturen Starter-planarkitekturen och Adobe Commerce på molninfrastrukturproffsens planarkitektur).

## Krav: SSH i din miljö

Om du vill dumpa din databas på Adobe Commerce i molninfrastrukturen med någon av de varianter som beskrivs i den här artikeln måste du först [SSH i din miljö](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).

>[!WARNING]
>
>Oavsett om du väljer Alternativ 1 eller Alternativ 2 ska du köra kommandot under tider med låg belastning mot en sekundär databasnod.

## Alternativ 1: db-dump (**e-postverktyg; rekommenderas**)

Du kan dumpa din databas med [ECE-verktyg](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) kommando:

```php
vendor/bin/ece-tools db-dump
```

Detta är det rekommenderade och säkraste alternativet.

Se [Dumpa databasen (ECE-Tools)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/database-dump.html) i vår Commerce on Cloud Infrastructure Guide.

## Alternativ 2: mysqldump

>[!WARNING]
>
>Kör inte det här kommandot mot databaskluster. Klustret skiljer inte åt om det körs mot den primära databasen eller mot en sekundär. Om klustret kör det här kommandot mot det primära, kommer databasen inte att kunna köra skrivningar förrän dumpningen är klar och kan påverka prestanda och webbplatsens stabilitet.

Du kan dumpa din databas med hjälp av den inbyggda MySQL `mysqldump` -kommando.

Hela kommandot kan se ut så här:

```sql
mysqldump -h <host> -u <username> -p <password> --single-transaction <db_name> | gzip > /tmp/<dump_name>.sql.gz
```

Databassäkerhetskopieringen som skapades genom att köra `mysqldump` kommando och sparad i `\tmp`, ska flyttas från den här platsen. Det ska inte ta upp lagringsutrymme i `\tmp` (vilket kan leda till problem).

Om du vill ha dina DB-autentiseringsuppgifter (värd, användarnamn och lösenord) kan du ringa `MAGENTO_CLOUD_RELATIONSHIPS` miljövariabel:

```
echo $MAGENTO_CLOUD_RELATIONSHIPS |base64 --d |json_pp
```

**Relaterad dokumentation:**

* [mysqldump - Ett program för säkerhetskopiering av databas](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) i officiell MySQL-dokumentation.
* [Molnspecifika variabler](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html) (se `MAGENTO_CLOUD_RELATIONSHIPS`) i vår Commerce on Cloud Infrastructure Guide.
