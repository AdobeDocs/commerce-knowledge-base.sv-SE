---
title: Återställ miljö på Adobe Commerce i molninfrastruktur
description: I den här artikeln visas olika scenarier för återställning av en miljö på Adobe Commerce i molninfrastruktur.
exl-id: e6b27838-ca1e-415f-a098-2aa2576e3f20
feature: Best Practices, Build, Cloud, Console
source-git-commit: ddde2385f1d94194b34e9ed51f6cbda55c916d90
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 0%

---

# Återställ miljö på Adobe Commerce i molninfrastruktur

I den här artikeln visas olika scenarier för återställning av en miljö på Adobe Commerce i molninfrastruktur.

Välj det alternativ som passar bäst:

* Om du har planerat en aktivitet (planerad driftsättning eller uppgradering) - [Scenario 1: Planerad aktivitet)](#scen1).
* Om du har en giltig ögonblicksbild - [Scenario 2: Återställ en ögonblicksbild](#scen2).
* Om du har en stabil version, men ingen giltig ögonblicksbild - [Scenario 3: Ingen ögonblicksbild, stabil konstruktion (SSH-anslutning tillgänglig)](#scen3).
* Om bygget är brutet och du inte har någon giltig ögonblicksbild - [Scenario 4: Ingen ögonblicksbild; bygg bruten (ingen SSH-anslutning)](#scen4).

## Scenario 1: Planerad aktivitet

Med en planerad driftsättning eller uppgradering är det enklaste och rekommenderade [!UICONTROL Rollback] som en del av dina förberedelser skulle det vara handlaren som skulle göra följande:

>[!NOTE]
>
>Testa alltid dessa steg i **[!UICONTROL Staging Environment]** först!

<u>Fem dagar före uppgraderings-/driftsättningsaktiviteterna</u>:

1. Kontrollera storleken på den aktuella databasen.
1. Kontrollera att det finns tillräckligt med diskutrymme på `/data/exports` för [!UICONTROL Database Dump]. Om det inte finns tillräckligt med diskutrymme kan du antingen ta bort oönskade data eller skapa ett supportärende och begära att skivan ska expanderas.

<u>På den dag då ändringarna görs</u>:

1. Placera webbplatsen på [!UICONTROL Maintenance Mode].<br>
Läs mer om [Aktivera eller inaktivera [!UICONTROL Maintenance Mode]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html) i vår användarhandbok, och [[!UICONTROL Maintenance Mode] alternativ för uppgradering](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/troubleshooting/maintenance-mode-options.html) i vår uppgraderingsguide.
1. Ta en lokal [[!UICONTROL Database Dump]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/create-database-dump-on-cloud.html).

<u>Om en [!UICONTROL Rollback] krävs</u>:

1. Om program som [!DNL MariaDB] har uppgraderats som en del av den planerade aktiviteten, har programmet installerats om till en tidigare version först.
1. [!UICONTROL Rollback] den lokala databasen [!UICONTROL Database Dump]och importera tillbaka det till [!DNL MariaDB].
1. [!UICONTROL Rollback] koden via [!DNL Git] till en tidigare arbetsversion.

Använda [!UICONTROL Snapshots] är inte det rekommenderade sättet för uppgradering/planerad aktivitet [!UICONTROL rollbacks/restores], eftersom det tar mycket längre tid att hämta data jämfört med en lokal [!UICONTROL Database Dump]som i steg 2 i **Om en [!UICONTROL Rollback] krävs** -avsnitt.

[!UICONTROL Snapshots] lagras inte på noden/servern, lagras i ett separat lagringsblock och eftersom dessa data måste överföras från blocklagringen via nätverket till en ny disk tar det tid i processen. Den nya disken monteras sedan på noden och är klar att hämtas/importeras till den ursprungliga disken som är ansluten till noden/servern.

När du jämför detta med att importera en lokal [!UICONTROL Database Dump]kan data redan hämtas på noden/servern, så mycket tid sparas bara som en [!UICONTROL Database Import] är obligatoriskt.

## Scenario 2: Återställ en ögonblicksbild

Läs: [Återställa en ögonblicksbild av Adobe Commerce i molninfrastrukturen](https://devdocs.magento.com/cloud/project/project-webint-snap.html#restore-snapshot) i vår dokumentation för utvecklare.

>[!NOTE]
>
>Att skapa en ögonblicksbild måste vara det första steget efter att du har öppnat Adobe Commerce på molninfrastrukturskontot och innan du kan göra större ändringar. Det är en god praxis och rekommenderas varmt.

Läs: [Skapa en fixering](https://devdocs.magento.com/cloud/project/project-webint-snap.html#create-snapshot) i vår dokumentation för utvecklare.

## Scenario 3: Ingen ögonblicksbild, stabil konstruktion (SSH-anslutning tillgänglig)

I det här avsnittet visas hur du återställer en miljö när du inte har skapat en ögonblicksbild men kan komma åt miljön via SSH.

Stegen är:

1. Inaktivera konfigurationshantering.
1. Avinstallera Adobe Commerce.
1. Återställ [!DNL git] gren.

När du har utfört dessa steg:

* Adobe Commerce-installationen återgår till Vanilla-läget (databasen återställd, distributionskonfigurationen borttagen, kataloger under `var` rensad).
* Dina [!DNL git] förgreningen har återställts till önskat läge tidigare.

Läs de detaljerade stegen nedan.

### Steg 0 (Förutsättning): Ta bort config.php för att inaktivera Configuration Management

Vi måste inaktivera Configuration Management så att den inte automatiskt tillämpar de tidigare konfigurationsinställningarna under distributionen.

Om du vill inaktivera konfigurationshantering måste du se till att `/app/etc/` katalogen innehåller inte `config.php` -fil.

Så här tar du bort konfigurationsfilen:

1. [SSH i din miljö](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Ta bort konfigurationsfilen: `rm app/etc/config.php`

Läs mer om konfigurationshantering:

* [Minska driftstoppen på Adobe Commerce i molninfrastrukturen](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) i vår kunskapsbas för support.
* [Konfigurationshantering för lagringsinställningar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) i vår dokumentation för utvecklare.

### Steg 1: Avinstallera Adobe Commerce med kommandot setup:uninstall


Om du avinstallerar Adobe Commerce tas databasen bort och återställs, distributionskonfigurationen tas bort och katalogerna rensas under `var`.

Läs: [Avinstallera Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html) i vår dokumentation för utvecklare.

Så här avinstallerar du Adobe Commerce:

1. [SSH i din miljö](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Kör `setup:uninstall` : `bin/magento setup:uninstall`
1. Bekräfta avinstallationen.

Följande meddelande visas för att bekräfta att avinstallationen lyckades:

```php
[SUCCESS]: Magento uninstallation complete.
```

Detta innebär att vi har återställt vår Adobe Commerce-installation (inklusive DB) till dess autentiska tillstånd (Vanilla).

### Steg 2: Återställ [!DNL git] bankkontor

Med [!DNL git] återställer vi tidigare koden till önskat läge.

1. Klona miljön i den lokala utvecklingsmiljön. Du kan kopiera kommandot i molnkonsolen:    ![copy_git_clone.png](assets/copy_git_clone.png)
1. Få åtkomst till implementeringshistoriken. Använd `--reverse` för att visa historiken i omvänd ordning för att underlätta: `git log --reverse`
1. Välj den implementeringshash som du har varit bra på. Om du vill återställa koden till dess autentiska läge (Vanilla), söker du efter den första implementeringen som skapade din gren (miljö).
   ![Välja en implementeringshash i Git-konsolen](assets/select_commit_hash.png)
1. Använd hårt [!DNL git] reset: `git reset --h <commit_hash>`
1. Skicka ändringar till servern: `git push --force <origin> <branch>`

När du har utfört dessa steg [!DNL git] grenen återställs och hela [!DNL git] Växelloggen är tydlig. Den sista [!DNL git] push utlöser omdistributionen för att tillämpa alla ändringar och installera om Adobe Commerce.

## Scenario 4: Ingen ögonblicksbild; bygge bruten (ingen [!DNL SSH] anslutning)

I det här avsnittet visas hur du återställer en miljö när den befinner sig i ett kritiskt tillstånd: Distributionsproceduren kan inte skapa ett fungerande program och därmed skapa [!DNL SSH] inte tillgänglig.

I det här fallet måste du först återställa arbetstillståndet i ditt Adobe Commerce-program med [!DNL git] återställ och sedan avinstallera Adobe Commerce (för att släppa och återställa databasen, ta bort distributionskonfigurationen osv.). Scenariot omfattar samma steg som i scenario 3, men stegordningen är annorlunda och det finns ytterligare ett steg - tvingad omdriftsättning. Stegen är:

1. [Återställ [!DNL git] gren.](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)
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

Om du kör `setup:uninstall` -kommandot misslyckas med ett fel och kan inte slutföras, vi kan rensa databasen manuellt med följande steg:

1. [SSH i din miljö](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Anslut till MySQL DB: `mysql -h database.internal` (För Pro-miljöer, se: [Konfigurera tjänsten MySQL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html)).
1. Släpp databasen \`main\`: `drop database main;`
1. Skapa en tom \`main\`-databas: `create database main;`
1. Ta bort följande konfigurationsfiler: `config.php` , `config.php` , `.bak,` , `env.php`, `env.php.bak`

När databasen har återställts [skapa [!DNL git] push to the environment to trigger redeploy](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli.html) och installera Adobe Commerce i en ny databas. eller [kör kommandot redeploy](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#environment-commands).
