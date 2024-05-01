---
title: Databasöverföringen förlorar anslutningen till MySQL
description: Den här artikeln innehåller en lösning för när databasöverföringen förlorar anslutningen till MySQL.
exl-id: 6051cea1-8292-4a81-8908-eb516cb4a32b
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Databasöverföringen förlorar anslutningen till MySQL

Den här artikeln innehåller en lösning för när databasöverföringen förlorar anslutningen till MySQL.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur 2.2.x, 2.3.x

## Problem

Databasen laddar inte upp till primär-/integreringsgrenar på Adobe Commerce på Cloud Infrastructure Pro-planarkitekturen eller någon gren på Adobe Commerce på Starter-planarkitekturen för molninfrastruktur, med symtomet att det inte går att ansluta. Det här felet visas i CLI.

```
web@ddc35c264bd89a72042f1f3e5a:~$ mysql -h database.internal -u user -p main
Enter password:
ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0 "Internal error/check (Not system error)"
```

## Orsak

Detta beror vanligtvis på att det inte finns tillräckligt med diskutrymme för att importera databasen.

## Lösning

Kontrollera om det inte finns tillräckligt med diskutrymme. Om du vill göra det kör du `netcat` i CLI mot databasporten 3306; ett meddelande visas om det är fullt:

```
web@ddc35c264bd89a72042f1f3e5a:~$ nc database.internal 3306
Database out of space
```

Du måste tilldela mer utrymme för databasen i `services.yaml` och distribuera om det finns utrymme som inte används. Om du vill se steg går du till [Diskutrymme för tjänst](https://devdocs.magento.com/cloud/project/manage-disk-space.html#service-disk-space).

Obs! I Pro-arkitekturplanen kan du kontrollera det tilldelade utrymmet på din partition genom att köra följande kommando: `df -h`

Förväntade utdata som liknar följande utdata. I det här exemplet används 10 GB av de 25 GB som allokerats, men 15 GB MySQL-utrymme används inte.

```
f240jestone3wt@i-087r2a25fdac80726:~$ df -h|grep 'File\|xvd'
Filesystem                                         Size  Used Avail Use% Mounted on
/dev/xvda1                                          59G   15G   42G  26% /
/dev/xvdj                                           25G   10G   15G  41% /data/mysql
/dev/xvdi                                           25G   22G  2.6G  90% /data/exports
```

## Relaterad läsning

[Hantera diskutrymme](https://devdocs.magento.com/cloud/project/manage-disk-space.html) i vår utvecklardokumentation
