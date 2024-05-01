---
title: Felsök fullständigt /tmp-paket för Adobe Commerce
description: Den här artikeln innehåller en lösning för när "/tmp"-monteringen är full, platsen kan vara nere och du inte kan lägga till SSH i en nod.
exl-id: e72d0f99-0060-474b-bb1c-2851896e1e43
feature: Storage
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# Felsök fullständigt /tmp-paket för Adobe Commerce

Den här artikeln innehåller en lösning för när `/tmp` monteringen är full, platsen kan vara nere och du kan inte lägga till SSH i en nod.

## Berörda produkter och versioner

* Adobe Commerce 2.3.0 - 2.3.6-p1, 2.4.0 - 2.4.2

## Problem

The `/tmp` Att vara full kan resultera i en rad möjliga symtom, bland annat följande fel:

* *SQLSTATE[HY000]: Allmänt fel: 3 Fel vid skrivning av fil*
* *Felkod: 28*
* *Inget utrymme kvar på enheten (28)*
* *error session_start(): failed: No space left on device*
* *FEL 1 (HY000): Det går inte att skapa/skriva till filen /tmp/*
* *SQL-fel: 3, SQLState: HY000*
* *Allmänt fel: 1021 Disken är full (/tmp)*
* *Det går inte att komma åt noden via SSH:*
  *bash: det går inte att skapa temporär fil för här-dokument: Det finns inget ledigt utrymme på enheten*
* *fel: 28&quot;Inget utrymme kvar på enheten&quot;*
* *mysqld: Disken är full med &quot;/tmp&quot;*
* *[FEL] mysqld: Disken är full (/tmp)*
* *SQLSTATE[HY000]: Allmänt fel: 1 Kan inte skapa/skriva till filen /tmp/*
* *SQLSTATE[HY000]: Allmänt fel: 23 Slut på resurser när filen &#39;/tmp/&#39; öppnas*
* *Felkod: 24&quot;För många öppna filer&quot;*
* *Fel: 23: Slut på resurser när filen öppnas*


<u>Steg som ska återskapas:</u>

Så här kontrollerar du hur full `/tmp` är, i CLI-omgången till `/tmp` och kör följande kommando:

```bash
 df -h
```

<u>Förväntat resultat</u>:

Mindre än 80 %.

<u>Faktiskt resultat</u>:

Cirka 100 %.

## Orsak

The `/tmp` Monteringen har för många filer, vilket kan bero på:

* Felaktiga SQL-frågor som genererar stora och/eller för många temporära tabeller.
* Tjänster som skriver till `/tmp` katalog.
* Säkerhetskopiering/dumpar av databaser finns kvar i `/tmp` katalog.

## Lösning

Det finns saker du kan göra för att frigöra lite utrymme en gång, och det finns bra metoder som förhindrar `\tmp` från att bli full.

### Kontrollera och frigöra noder

Se till att det finns tillräckligt med tillgängliga noder. Kör följande kommando för att göra detta:

```bash
df -i
```

Utdata skulle se ut ungefär så här:

```bash
Filesystem Inodes   Used   Free Use% Mounted on
/dev/nvme2n1 655360    1695  653665    1% /data/mysql
```

Kontrollera att Use% är &lt;70%. Inoder är korrelerade med filer. Om du tar bort filer från partitionen kommer du att frigöra noder.

### Kontrollera och frigör lagringsutrymme

Det finns flera tjänster som kan spara filer i `/tmp`.

#### Kontrollera och frigör MySQL-utrymme

Följ instruktionerna i [Utrymmet för MySQL-disken är lågt på Adobe Commerce i molninfrastrukturen > Kontrollera och frigör lagringsutrymme](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md#check_and_free) i vår kunskapsbas för support.

#### Kontrollera Elasticsearch-heapdumpar

>[!WARNING]
>
>Det finns loggningsinformation som kan vara användbar för att undersöka problem. Överväg att lagra dem på en separat plats i minst 10 dagar.

Ta bort stackar (`*.hprof`) med systemgränssnitt:

```bash
find /tmp/*.hprof -type f -delete
```

Om du inte har behörighet att ta bort filer som har skapats av en annan användare (i det här fallet Elasticsearch), men du ser att filerna är stora, [skapa en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) för att ta hand om dem.

#### Kontrollera databasdumpar/säkerhetskopior

>[!WARNING]
>
>Säkerhetskopiering av databaser skapas vanligtvis i ett syfte. Om du är osäker på om filen fortfarande behövs kan du överväga att flytta den till en annan plats i stället för att ta bort den.

Kontrollera `/tmp` for `.sql` eller `.sql.gz` och rensa dem. Dessa kan ha skapats med andra verktyg vid säkerhetskopiering eller när databasdumpar skapas manuellt med hjälp av `mysqldump` verktyg.

### God praxis

Undvik problem med `/tmp` Följ dessa rekommendationer när du är full:

* Använd inte MySQL för sökning. Elasticsearch för sökning eliminerar vanligtvis behovet av de flesta komplicerade temporära tabellskapanden. Se [Konfigurera Adobe Commerce att använda Elasticsearch](https://devdocs.magento.com/guides/v2.2/config-guide/elasticsearch/configure-magento.html) i vår dokumentation för utvecklare.
* Undvik att köra `SELECT` fråga om kolumner utan index, eftersom detta använder mycket temporärt diskutrymme. Du kan också lägga till index.
* Skapa en kron att rensa upp `/tmp` genom att köra följande kommando i CLI:

  ```bash
  sudo find /tmp -type f -atime +10 -delete
  ```

## Relaterad läsning

[Det är ont om diskutrymme på Adobe Commerce i molninfrastrukturen](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) i vår kunskapsbas för support.
