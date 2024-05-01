---
title: Uppgradera MariaDB 10.0 till 10.2 för Adobe Commerce i molnet
description: MariaDB 10.0 och 10.1 är EOL. [Supporten upphörde den 31 mars 2019 respektive den 17 oktober 2020](https://endoflife.date/mariadb). I den här artikeln beskrivs hur du uppgraderar MariaDB från 10.0 till 10.2 eller 10.2 till 10.3 eller till 10.4 för att kunna använda Adobe Commerce i molninfrastrukturen.
exl-id: bf66798b-f05c-482f-a2b4-b9bef92b0bab
feature: Best Practices, Cloud
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# Uppgradera MariaDB 10.0 till 10.2 för Adobe Commerce i molnet

MariaDB 10.0 och 10.1 är EOL. [Supporten upphörde den 31 mars 2019 respektive den 17 oktober 2020](https://endoflife.date/mariadb). I den här artikeln beskrivs hur du uppgraderar MariaDB från 10.0 till 10.2 eller 10.2 till 10.3 eller till 10.4 för att kunna använda Adobe Commerce i molninfrastrukturen.

>[!NOTE]
>
>MariaDB 10.0 är ett EOL-system (End-of-life) och stöds inte i nuvarande Adobe Commerce-versioner. Det är bäst att avinstallera alla versioner av ledningscentralen inom 30 dagar från det att de har hämtats.

## Berörda produkter och versioner

* MariaDB 10.2 rekommenderas för Adobe Commerce i molninfrastruktur 2.3.x.
* MariaDB 10.4 rekommenderas för 2.4.x. MariaDB 10.3 är även kompatibel med Adobe Commerce i molninfrastruktur 2.4.x.

## Uppgradera steg

Om du vill uppgradera från MariaDB 10.0 till 10.2 eller 10.2 till 10.3 eller till 10.4 utför du följande steg:

1. Skapa en [DB-säkerhetskopiering med kommandon för DB-säkerhetskopiering i ECE-Tools](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump). Detta måste göras före steg 2 och 3 om något går fel när tabeller/rader uppdateras.
1. [Kontrollera och konvertera alla kompakta tabeller till dynamiska tabeller](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html). Detta krävs för att undvika eventuell dataförlust under databasuppgraderingen.
1. Sök efter MYISAM-tabeller. Du måste [konvertera alla MyISAM-tabeller till InnoD](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html).
1. När du har förberett databastabellerna och raderna (de två föregående stegen) skapar du en [DB-säkerhetskopiering med kommandon för DB-säkerhetskopiering i ECE-Tools](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump).
1. [Öppna en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) för att schemalägga uppgraderingen från MariaDB 10.0 till 10.2 eller 10.2 till 10.3 eller 10.4. I detaljinfo om biljett datum och tid när du vill att databasen ska uppgraderas. Supportteamet behöver 48 timmars varsel och handlarnas dev-team måste vara tillgängliga. När du har kommit överens om tid och datum för uppgraderingen gör du följande:
   1. Försätt platsen i underhållsläge och stoppa alla DB-aktiviteter, t.ex. crons.
   1. Skapa en [DB-säkerhetskopiering med kommandon för DB-säkerhetskopiering i ECE-Tools](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump).
   1. Informera supporten om att du har slutfört säkerhetskopieringen. Gör detta via supportbiljetten. Information om hur du visar och spårar dina biljetter finns i [Användarhandbok för Adobe Commerce Help Center: Spåra biljetter](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) i vår kunskapsbas för support.
   1. Adobe Commerce supportteam kommer att påbörja uppgraderingen av MariaDB. Om alla ovanstående steg har utförts och databasen har en genomsnittlig storlek, kan detta göras på ungefär en timme. Större DB:er tar längre tid. Du får information via din biljett när uppgraderingen är klar.
1. Inaktivera underhållsläge. Se [Aktivera eller inaktivera underhållsläge](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html#instgde-cli-maint) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om krav för Adobe Commerce 2.4.x finns i [Systemkrav för Adobe Commerce 2.4 > Databas](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html#database) i vår dokumentation för utvecklare.
