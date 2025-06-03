---
title: Återställ miljö på Adobe Commerce i molninfrastruktur
description: I den här artikeln visas olika scenarier för återställning av en miljö på Adobe Commerce i molninfrastruktur.
exl-id: e6b27838-ca1e-415f-a098-2aa2576e3f20
feature: Best Practices, Build, Cloud, Console
source-git-commit: 4327f464fb8eebf30a380e9e58afe55c3e613e52
workflow-type: tm+mt
source-wordcount: '1110'
ht-degree: 0%

---

# Återställ miljö på Adobe Commerce i molninfrastruktur

I den här artikeln visas olika scenarier för återställning av en miljö på Adobe Commerce i molninfrastruktur.
>[!NOTE]
>
>Den här guiden gäller alla Cloud Starter-miljöer och endast integreringsmiljöer i Cloud Pro.

Välj det alternativ som passar bäst:

* Om du har planerad aktivitet (planerad distribution eller uppgradering) - [Scenario 1: planerad aktivitet)](#scen1).
* Om du har en giltig ögonblicksbild - [Scenario 2: Återställ en ögonblicksbild](#scen2).
* Om du har ett stabilt bygge, men ingen giltig ögonblicksbild - [Scenario 3: Ingen ögonblicksbild, bygg en stabil (SSH-anslutning tillgänglig)](#scen3).
* Om bygget är brutet och du inte har någon giltig ögonblicksbild - [Scenario 4: Ingen ögonblicksbild, bygg bruten (ingen SSH-anslutning)](#scen4).

## Scenario 1: Planerad aktivitet

Med en planerad driftsättning eller uppgradering är det enklaste och rekommenderade [!UICONTROL Rollback] att handlaren, som en del av dina förberedelser, gör följande:

>[!NOTE]
>
>Testa alltid de här stegen i den nedre miljön först!

<u>Fem dagar före uppgraderings-/distributionsaktiviteterna</u>:

1. Kontrollera storleken på den aktuella databasen.
1. Kontrollera att det finns tillräckligt med diskutrymme på `/data/exports` för att rymma en [!UICONTROL Database Dump]. Om det inte finns tillräckligt med diskutrymme kan du antingen ta bort oönskade data eller skapa ett supportärende och begära att skivan ska expanderas.

<u>På dagen för ändringarna</u>:

1. Placera webbplatsen i [!UICONTROL Maintenance Mode].
Läs mer om [Aktivera eller inaktivera [!UICONTROL Maintenance Mode]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html?lang=sv-SE) i vår användarhandbok och [[!UICONTROL Maintenance Mode] alternativ för uppgradering](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/troubleshooting/maintenance-mode-options.html?lang=sv-SE) i vår uppgraderingsguide.
1. Inaktivera cron-jobb. Läs mer om hur du inaktiverar cron-jobb i vår [egenskapsguide](<https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property#disable-cron-jobs>) för cron.
1. Ta en lokal [[!UICONTROL Database Dump]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/create-database-dump-on-cloud.html?lang=sv-SE).

<u>Om [!UICONTROL Rollback] krävs</u>:

1. Om program som [!DNL MariaDB] uppgraderades som en del av den planerade aktiviteten måste du först installera om programmet till en tidigare version.
1. [!UICONTROL Rollback] databasen som använder den lokala [!UICONTROL Database Dump] och importera den tillbaka till [!DNL MariaDB].
1. [!UICONTROL Rollback] koden via [!DNL Git] till en tidigare arbetsversion.

Att använda [!UICONTROL Snapshots] är inte det rekommenderade sättet för uppgradering/planerad aktivitet [!UICONTROL rollbacks/restores], eftersom det tar mycket längre tid att hämta data jämfört med en lokal [!UICONTROL Database Dump], som i steg 2 i avsnittet **Om [!UICONTROL Rollback] krävs**.

[!UICONTROL Snapshots] finns inte på noden/servern, de finns i ett separat lagringsblock och eftersom dessa data måste överföras från blocklagringen över nätverket till en ny disk tar det tid i processen. Den nya disken monteras sedan på noden och är klar att hämtas/importeras till den ursprungliga disken som är ansluten till noden/servern.

När du jämför detta med att importera en lokal [!UICONTROL Database Dump] går det redan att hämta data på noden/servern, så mycket tid sparas eftersom bara [!UICONTROL Database Import] krävs.

## Scenario 2: Återställ en ögonblicksbild

Läs: [Återställ en ögonblicksbild av Adobe Commerce i molninfrastrukturen](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-snapshot) i utvecklardokumentationen.

>[!NOTE]
>
>Att skapa en ögonblicksbild måste vara det första steget efter att du har öppnat Adobe Commerce på molninfrastrukturskontot och innan du kan göra större ändringar. Det är en god praxis och rekommenderas varmt.

Läs: [Skapa en ögonblicksbild](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#create-snapshot) i utvecklardokumentationen.

## Scenario 3: Ingen ögonblicksbild, stabil konstruktion (SSH-anslutning tillgänglig)

I det här avsnittet visas hur du återställer en miljö när du inte har skapat en ögonblicksbild men kan komma åt miljön via SSH.

Stegen är:

1. Inaktivera konfigurationshantering.
1. Avinstallera Adobe Commerce.
1. Återställ grenen [!DNL git].

När du har utfört dessa steg:

* Adobe Commerce-installationen återgår till sitt vaniläge (databasen återställd, distributionskonfigurationen borttagen, kataloger under `var` rensad).
* Din [!DNL git]-gren har återställts till önskat tillstånd tidigare.

Läs de detaljerade stegen nedan.

### Steg 0 (Förutsättning): Ta bort config.php för att inaktivera Configuration Management

Vi måste inaktivera Configuration Management så att den inte automatiskt tillämpar de tidigare konfigurationsinställningarna under distributionen.

Om du vill inaktivera Configuration Management kontrollerar du att katalogen `/app/etc/` inte innehåller filen `config.php`.

Så här tar du bort konfigurationsfilen:

1. [SSH till din miljö](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=sv-SE).
1. Ta bort konfigurationsfilen: `rm app/etc/config.php`

Läs mer om konfigurationshantering:

* [Minska driftsättningsdriftsavbrotten på Adobe Commerce i molninfrastrukturen](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) i vår kunskapsbas för support.
* [Konfigurationshantering för butiksinställningar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=sv-SE) i utvecklardokumentationen.

### Steg 1: Avinstallera Adobe Commerce med kommandot setup:uninstall


Om du avinstallerar Adobe Commerce-programvaran tas databasen bort och återställs, distributionskonfigurationen tas bort och katalogerna under `var` rensas.

Läs: [Avinstallera Adobe Commerce-programmet](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html?lang=sv-SE) i utvecklardokumentationen.

Så här avinstallerar du Adobe Commerce:

1. [SSH till din miljö](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=sv-SE).
1. Kör `setup:uninstall` : `bin/magento setup:uninstall`
1. Bekräfta avinstallationen.

Följande meddelande visas för att bekräfta att avinstallationen lyckades:

```php
[SUCCESS]: Magento uninstallation complete.
```

Detta innebär att vi har återställt vår Adobe Commerce-installation (inklusive DB) till dess autentiska tillstånd (Vanilla).

### Steg 2: Återställ grenen [!DNL git]

Med [!DNL git] återställd återställer vi koden till önskat läge tidigare.

1. Klona miljön i den lokala utvecklingsmiljön. Du kan kopiera kommandot i molnkonsolen:    ![copy_git_clone.png](assets/copy_git_clone.png)
1. Få åtkomst till implementeringshistoriken. Använd `--reverse` om du vill visa historik i omvänd ordning för att underlätta: `git log --reverse`
1. Välj den implementeringshash som du har varit bra på. Om du vill återställa koden till dess autentiska läge (Vanilla), söker du efter den första implementeringen som skapade din gren (miljö).
   ![Alt-text](image.png)
1. Använd hård [!DNL git]-återställning: `git reset --h <commit_hash>`
1. Skicka ändringar till servern: `git push --force <origin> <branch>`

När du har utfört de här stegen återställs vår [!DNL git]-gren och hela [!DNL git]-ändringsloggen är rensad. Den senaste [!DNL git]-push-åtgärden utlöser omdistributionen för att tillämpa alla ändringar och installera om Adobe Commerce.

## Scenario 4: Ingen ögonblicksbild; bygg bruten (ingen [!DNL SSH]-anslutning)

I det här avsnittet visas hur du återställer en miljö när den är i ett kritiskt tillstånd: Distributionsproceduren kan inte skapa ett fungerande program, vilket gör att anslutningen [!DNL SSH] inte är tillgänglig.

I det här fallet måste du först återställa arbetstillståndet för ditt Adobe Commerce-program med [!DNL git] reset och sedan avinstallera Adobe Commerce-programmet (för att släppa och återställa databasen, ta bort distributionskonfigurationen osv.). Scenariot omfattar samma steg som i scenario 3, men stegordningen är annorlunda och det finns ytterligare ett steg - tvingad omdriftsättning. Stegen är:

1. [Återställ  [!DNL git] förgreningen.](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)
1. [Inaktivera konfigurationshantering.](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)
1. [Avinstallera Adobe Commerce.](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)
1. Tvinga omdistribution.

När du har utfört dessa steg får du samma resultat som i scenario 3.

### Steg 4: Tvinga omdistribution

Gör en implementering (detta kan vara en tom implementering, men vi rekommenderar den inte) och skicka den till servern för att utlösa en omdistribution:

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## Återställ databasen manuellt om installationen misslyckas

Om körningen av kommandot `setup:uninstall` misslyckas med ett fel och inte kan slutföras, kan vi rensa databasen manuellt med följande steg:

1. [SSH till din miljö](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=sv-SE).
1. Anslut till MySQL-databasen: `mysql -h database.internal` (för Pro-miljöer, se: [Konfigurera MySQL-tjänsten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html?lang=sv-SE)).
1. Släpp `main` DB: `drop database main;`
1. Skapa en tom `main`-databas: `create database main;`
1. Ta bort följande konfigurationsfiler: `config.php`, `config.php.bak`, `env.php`, `env.php.bak`

När du har återställt databasen [gör du en [!DNL git] push till miljön för att aktivera omdistributionen](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli.html?lang=sv-SE) och installera Adobe Commerce till en ny databas. Eller [kör kommandot för omdistribution](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html?lang=sv-SE#environment-commands).
