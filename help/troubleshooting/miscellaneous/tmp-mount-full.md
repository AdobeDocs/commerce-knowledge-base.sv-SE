---
title: Felsök fullständigt /tmp-paket för Adobe Commerce
description: Den här artikeln innehåller en lösning för när "/tmp"-monteringen är full, platsen kan vara nere och du inte kan lägga till SSH i en nod.
exl-id: e72d0f99-0060-474b-bb1c-2851896e1e43
feature: Storage
role: Developer
source-git-commit: aa4cfbceb745f1a06b8a8f9e93cbdebbc151458b
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# Felsök fullständigt /tmp-paket för Adobe Commerce

Den här artikeln innehåller en lösning för när monteringen av `/tmp` är full, platsen kan vara nere och du inte kan lägga till SSH i en nod.

## Berörda produkter och versioner

* Adobe Commerce 2.3.0 - 2.3.6-p1, 2.4.0 - 2.4.2

## Problem

Det fullständiga monteringsvärdet `/tmp` kan resultera i en rad möjliga symtom, bland annat följande fel:

* *SQLSTATE[HY000]: Allmänt fel: 3 Fel vid skrivning av fil*
* *Felkod: 28*
* *Inget utrymme kvar på enheten (28)*
* *error session_start(): failed: No space left on device*
* *FEL 1 (HY000): Det går inte att skapa/skriva till filen /tmp/*
* *SQL-fel: 3, SQLState: HY000*
* *Allmänt fel: 1021 Disken är full (/tmp)*
* *Det går inte att komma åt noden via SSH:*
  *bash: det går inte att skapa temporär fil för här-dokument: Det finns inget ledigt utrymme på enheten*
* *fel: 28&quot;Inget utrymme återstår på enheten&quot;*
* *mysqld: Disken är full med &quot;/tmp&quot;*
* *[FEL] mysqld: Disken är full (/tmp)*
* *SQLSTATE[HY000]: Allmänt fel: 1 Det går inte att skapa/skriva till filen /tmp/*
* *SQLSTATE[HY000]: Allmänt fel: 23 Slut på resurser när filen /tmp/* öppnas
* *Felkod: 24&quot;För många öppna filer&quot;*
* *Allvarligt fel: 23: Resurser saknas när filen öppnas*


<u>Steg att återskapa:</u>

Om du vill kontrollera hur full monteringen av `/tmp` är växlar du i CLI till `/tmp` och kör följande kommando:

```bash
 df -h
```

<u>Förväntat resultat</u>:

Mindre än 80 %.

<u>Faktiskt resultat</u>:

Cirka 100 %.

## Orsak

Monteringen `/tmp` har för många filer, vilket kan bero på:

* Felaktiga SQL-frågor som genererar stora och/eller för många temporära tabeller.
* Tjänster skriver till katalogen `/tmp`.
* Databassäkerhetskopior/dumpar finns kvar i katalogen `/tmp`.

## Lösning

Det finns saker du kan göra för att frigöra lite utrymme en gång, och det finns god praxis som förhindrar `\tmp` från att bli full.

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

Det finns flera tjänster som kanske sparar filer i `/tmp`.

#### Kontrollera och frigör MySQL-utrymme

Följ instruktionerna i [MySQL-diskutrymmet har slut på Adobe Commerce i molninfrastrukturen > Kontrollera och frigör lagringsutrymme](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27806#check-and-free-up-storage-space) i vår supportkunskapsbas.

#### Kontrollera Elasticsearch-hjälptexter

>[!WARNING]
>
>Det finns loggningsinformation som kan vara användbar för att undersöka problem. Överväg att lagra dem på en separat plats i minst 10 dagar.

Ta bort stackar (`*.hprof`) med systemgränssnitt:

```bash
find /tmp/*.hprof -type f -delete
```

Om du inte har behörighet att ta bort filer som har skapats av en annan användare (i det här fallet Elasticsearch), men du ser att filerna är stora, [skapar du en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) för att hantera dem.

#### Kontrollera databasdumpar/säkerhetskopior

>[!WARNING]
>
>Säkerhetskopiering av databaser skapas vanligtvis i ett syfte. Om du är osäker på om filen fortfarande behövs kan du överväga att flytta den till en annan plats i stället för att ta bort den.

Kontrollera `/tmp` efter `.sql`- eller `.sql.gz`-filer och rensa dem. Dessa kan ha skapats med andra verktyg under säkerhetskopieringen eller när databasdumpar skapades manuellt med verktyget `mysqldump`.

### God praxis

Följ de här rekommendationerna för att undvika att få problem med att `/tmp` är full:

* Använd inte MySQL för sökning. Elasticsearch för sökningar eliminerar vanligtvis behovet av de flesta komplicerade temporära tabellskapanden. Se [Konfigurera Adobe Commerce att använda Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/configure-search-engine) i utvecklardokumentationen.
* Undvik att köra `SELECT`-frågan på kolumner utan index eftersom det här kräver mycket temporärt diskutrymme. Du kan också lägga till index.
* Skapa en cron för att rensa upp `/tmp` genom att köra följande kommando i CLI:

  ```bash
  sudo find /tmp -type f -atime +10 -delete
  ```

## Relaterad läsning

[Det är ont om diskutrymme på MySQL på Adobe Commerce i molninfrastrukturen](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27806) i vår kunskapsbas för support.
