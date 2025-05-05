---
title: Uppgradera MariaDB 10.4 till 10.5 för Adobe Commerce i molnet
description: MariaDB 10.4 upphör den 18 juni 2024. I den här artikeln beskrivs hur du uppgraderar MariaDB från 10.4 till 10.5 för att fortsätta använda Adobe Commerce i molninfrastrukturen.
feature: Best Practices, Cloud
exl-id: 065840b8-28c1-4686-95fc-df3e73152845
source-git-commit: 11f2fae3264a61413c5da1b93ef4980151a1df1e
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Uppgradera MariaDB 10.4 till 10.5 för Adobe Commerce i molnet

MariaDB är en öppen källkodsdatabas som används med Adobe Commerce.

MariaDB 10.4 upphör med supporten den [18 juni 2024](https://endoflife.date/mariadb). Du är inte längre PCI-kompatibel när du använder en version av MariaDB som inte stöds. I den här artikeln beskrivs hur du uppgraderar från MariaDB 10.4 till 10.5 för att fortsätta använda Adobe Commerce i molninfrastrukturen.

>[!NOTE]
>
>Eftersom MariaDB 10.4 når slutet av livscykeln (EOL) stöds den inte längre i nuvarande Adobe Commerce-versioner. Det är bäst att avinstallera alla versioner av ledningscentralen inom 30 dagar från det att de har hämtats.

## Berörda produkter och versioner

* Alla Adobe Commerce lokalt och i molninfrastrukturen 2.4.4 och 2.4.5

## Lösning

Använd de nya patcharna (2.4.4-p9 eller 2.4.5-p8) som släpps den 11 juni 2024 för att säkerställa kompatibilitet med MariaDB 10.5. Följ sedan stegen nedan för att uppgradera från MariaDB 10.4 till 10.5.

### Uppgradera steg för molndistributioner

1. Skapa en [DB-säkerhetskopia med hjälp av kommandona för DAB-säkerhetskopiering i ECE-Tools ](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/storage/snapshots). Säkerhetskopieringen måste utföras före steg 2 och 3 om något går fel när tabeller/rader uppdateras.
1. [Kontrollera och konvertera alla kompakta tabeller till dynamiska tabeller](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/maintenance/mariadb-upgrade). Det här steget krävs för att undvika eventuell dataförlust under databasuppgraderingen.
1. Sök efter MYISAM-tabeller. Du måste [konvertera alla MyISAM-tabeller till InnoD](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud).
1. När du har förberett databastabellerna och raderna (de två föregående stegen) skapar du en [DB-säkerhetskopia med hjälp av kommandona för DB-säkerhetskopiering i ECE-Tools](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
1. [Öppna en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) för att schemalägga uppgraderingen från MariaDB 10.4 till 10.5. I biljetten anger du datum och tid när du vill att databasen ska uppgraderas. Supportteamet behöver 48 timmars varsel och handlarens utvecklingsgrupp måste vara tillgänglig. När du har kommit överens om tid och datum för uppgraderingen gör du följande:
   1. Försätt platsen i underhållsläge och stoppa alla DB-aktiviteter, till exempel crons.
   1. Skapa en [DB-säkerhetskopia med hjälp av kommandona för DAB-säkerhetskopiering i ECE-Tools ](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
   1. Informera supporten om att du har slutfört säkerhetskopieringen via din supportanmälan. Information om hur du visar och spårar biljetter finns i [Adobe Commerce Help Center User Guide: Track your Tickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) i vår kunskapsbas för support.
   1. Adobe Commerce supportteam påbörjar sedan uppgraderingsprocessen till MariaDB. Om alla ovanstående steg har utförts och databasen har en genomsnittlig storlek tar processen ca en timme. Större DB tar längre tid. När uppgraderingen är klar får du information via din biljett.
1. Inaktivera underhållsläge. Mer information finns i [Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i utvecklardokumentationen.

>[!NOTE]
>
>Vi rekommenderar att du skapar en DB-säkerhetskopia före och efter varje uppgraderingssteg för att eliminera risken för dataförlust. Detta gör att du kan gå tillbaka till ett tidigare steg om det uppstår problem under uppgraderingen.

## Relaterad läsning

* [Guide för bästa praxis för databasuppgradering](https://experienceleague.adobe.com/sv/docs/commerce-operations/upgrade-guide/prepare/prerequisites) för lokala distributioner.
* [Uppgradera MariaDB 10.0 till 10.2 för Adobe Commerce i molnet](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10-0-to-10-2-for-magento-commerce-cloud) i vår kunskapsbas för support.
* [Adobe Commerce livscykelpolicy](https://experienceleague.adobe.com/sv/docs/commerce-operations/release/planning/lifecycle-policy) i utvecklardokumentationen.
