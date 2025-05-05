---
title: Återställningsmiljö utan ögonblicksbild i molnet
description: I den här artikeln beskrivs två lösningar för att återställa en miljö utan att du behöver ha en ögonblicksbild av din miljö på Adobe Commerce i molninfrastruktur.
exl-id: 834d13a7-3b1a-460c-9ed0-9d560105f436
feature: Build, Cloud, Console
source-git-commit: 5347e8714ef1374440f5d246100a0221e4b189fc
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# Återställningsmiljö utan ögonblicksbild i molnet

I den här artikeln beskrivs två lösningar för att återställa en miljö utan att du behöver ha en ögonblicksbild av din miljö på Adobe Commerce i molninfrastruktur.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur, [alla versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Välj det alternativ som passar bäst:

* Om du har ett stabilt bygge, men ingen giltig ögonblicksbild - [Scenario 1: Ingen ögonblicksbild, bygg en stabil (SSH-anslutning tillgänglig)](#scen2).
* Om bygget är brutet och du inte har någon giltig ögonblicksbild - [Scenario 2: Ingen ögonblicksbild, bygg bruten (ingen SSH-anslutning)](#scen3).

## Scenario 1: Ingen ögonblicksbild, stabil konstruktion (SSH-anslutning tillgänglig) {#scen2}

I det här avsnittet visas hur du återställer en miljö när du inte har skapat en ögonblicksbild men kan komma åt miljön via SSH.

Stegen är:

1. Inaktivera konfigurationshantering.
1. Avinstallera Adobe Commerce.
1. Återställ Git-grenen.

När du har utfört dessa steg:

* Adobe Commerce-installationen återgår till Vanilla-läget (databasen återställd, distributionskonfigurationen borttagen, kataloger under `var` rensad)
* Git-grenen har återställts till det önskade läget tidigare

Läs de detaljerade stegen nedan:

### Steg 0 (Förutsättning): Ta bort config.php för att inaktivera Configuration Management {#disable_config_management}

Vi måste inaktivera Configuration Management så att den inte automatiskt tillämpar de tidigare konfigurationsinställningarna under distributionen.

Om du vill inaktivera Configuration Management kontrollerar du att katalogen `/app/etc/` inte innehåller filerna `config.php` (för Adobe Commerce 2.4.x) eller `config.local.php` (för Adobe Commerce 2.1.x).

Så här tar du bort konfigurationsfilen:

1. [SSH till din miljö](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Ta bort konfigurationsfilen:
   * För Adobe Commerce 2.4:

   ```php
    rm app/etc/config.php
   ```

   * För Adobe Commerce 2.1:

   ```php
     rm app/etc/config.local.php
   ```

Läs mer om konfigurationshantering genom att läsa:

* [Minska driftsättningsdriftsavbrotten på Adobe Commerce i molninfrastrukturen](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) i vår kunskapsbas för support.
* [Konfigurationshantering för butiksinställningar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) i utvecklardokumentationen.

### Steg 1: Avinstallera Adobe Commerce med kommandot setup:uninstall {#setup-uninstall}


Om du avinstallerar Adobe Commerce-programvaran tas databasen bort och återställs, distributionskonfigurationen tas bort och katalogerna under `var` rensas.

Granska [Avinstallera Adobe Commerce-programmet](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html) i utvecklardokumentationen.

Så här avinstallerar du Adobe Commerce:

1. [SSH till din miljö](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Kör `setup:uninstall`:

   ```php
     php bin/magento setup:uninstall
   ```

1. Bekräfta avinstallationen.

Följande meddelande visas för att bekräfta att avinstallationen lyckades:

```php
[SUCCESS]: Magento uninstallation complete.
```

Detta innebär att vi har återställt vår Adobe Commerce-installation (inklusive DB) till dess autentiska tillstånd (Vanilla).

### Steg 2: Återställ Git-grenen {#reset-git-branch}

Med Git-återställning återställer vi koden till önskat läge tidigare.

1. Klona miljön i den lokala utvecklingsmiljön. Du kan kopiera kommandot i molnkonsolen:    ![copy_git_clone.png](assets/copy_git_clone.png)
1. Få åtkomst till implementeringshistoriken. Använd `--reverse` om du vill visa historiken i omvänd ordning för att underlätta:

   ```git
     git log --reverse
   ```

1. Välj den implementeringshash som du har varit bra på. Om du vill återställa koden till dess autentiska läge (Vanilla), söker du efter den första implementeringen som skapade din gren (miljö).    ![Välja en implementeringshash i Git-konsolen](assets/select_commit_hash.png)
1. Använd återställning av hårddiskutrymme:

   ```git
     git reset --h <commit_hash>
   ```

1. Skicka ändringar till servern:

   ```git
     git push --force <origin> <branch>
   ```

När du har utfört de här stegen återställs Git-grenen och hela Git-ändringsloggen är klar. Den sista Git-push-åtgärden utlöser omdistributionen för att tillämpa alla ändringar och installera om Adobe Commerce.

## Scenario 2: Ingen ögonblicksbild; bygg bruten (ingen SSH-anslutning) {#scen3}

I det här avsnittet visas hur du återställer en miljö när den befinner sig i ett kritiskt tillstånd: Distributionsproceduren kan inte skapa ett fungerande program, vilket gör att SSH-anslutningen inte är tillgänglig.

I det här fallet måste du först återställa arbetstillståndet för ditt Adobe Commerce-program med Git-återställning och sedan avinstallera Adobe Commerce-programmet (för att släppa och återställa databasen, ta bort distributionskonfigurationen osv.). Scenariot omfattar samma steg som i scenario 1, men stegordningen är annorlunda och det finns ytterligare ett steg - tvingad omdriftsättning. Stegen är:

[1. Återställ Git-grenen.](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)

[2. Inaktivera konfigurationshantering.](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)

[3. Avinstallera Adobe Commerce.](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)

4&period; Tvinga omdistribution.

När du har utfört dessa steg får du samma resultat som i scenario 1.

### Steg 4: Tvinga omdistribution

Gör en implementering (detta kan vara en tom implementering, men vi rekommenderar den inte) och skicka den till servern för att utlösa en omdistribution:

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## Återställ databasen manuellt om installationen misslyckas

Om körningen av kommandot `setup:uninstall` misslyckas med ett fel och inte kan slutföras, kan vi rensa databasen manuellt med följande steg:

1. [SSH till din miljö](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Anslut till MySQL DB:

   ```sql
   mysql -h database.internal
   ```

1. Släpp `main`-databasen:

   ```sql
   drop database main;
   ```

1. Skapa en tom `main`-databas:

   ```sql
   create database main;
   ```

1. Ta bort följande konfigurationsfiler: `config.php`, `config.php` `.bak`, `env.php` och `env.php.bak`.

När du har återställt databasen gör [en Git-överföring till miljön för att utlösa omdistributionen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#git-commands) och installera Adobe Commerce till en nyligen skapad DB. Eller [kör kommandot för omdistribution](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#environment-commands).

## Relaterad läsning

I vår utvecklardokumentation:

* [Återställ en ögonblicksbild i molnet](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup)
* [Skapa en ögonblicksbild](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#create-a-manual-backup)
* [Fixeringar och hantering av säkerhetskopior](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)
* [Hantera grenar med molnkonsolen - Visa loggar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html?lang=en#view-logs)
* [Komponentdistributionsfel](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/recover-failed-deployment.html)
* [Hantera ditt projekt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project)
