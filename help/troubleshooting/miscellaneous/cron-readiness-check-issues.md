---
title: Problem med beredskapskontroll av kron
description: "Den här artikeln innehåller lösningar på viktiga beredskapsproblem. Följande är symtom på kronproblem:"
exl-id: 1f2cee2c-98ad-4cf5-af16-d736fced2a15
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Problem med beredskapskontroll av kron

Den här artikeln innehåller lösningar på problem med viktig beredskap. Följande är symtom på kronproblem:

* Ett felmeddelande om PHP-inställningen `$HTTP_RAW_POST_DATA` visas trots att den är korrekt inställd.
* PHP-beredskapskontrollen visar inte PHP-versionen som i följande bild:
  ![upgr-tshot-no-cron.png](assets/upgr-tshoot-no-cron.png)
* Följande fel visas i Commerce Admin:
  ![compman-cron-not-running.png](assets/compman-cron-not-running.png)
Du kan behöva klicka på **Systemmeddelanden** högst upp i fönstret enligt följande:
  ![compman_sys-messages.png](assets/compman_sys-messages.png)

## Kontrollera din befintliga crontab {#check-your-existing-crontab}

I det här avsnittet beskrivs hur du ser om cron körs och hur du kontrollerar om det är korrekt konfigurerat.

Så här kontrollerar du om din crontab är inställd:

1. Logga in på din Commerce-server som eller växla till [Magento filsystemägare](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html).
1. Kontrollera om följande fil finns: `$ ls -al <magento_root>/var/.setup_cronjob_status`. Om filen finns har cron körts tidigare. Om filen *inte* finns, antingen har du inte installerat Adobe Commerce än eller så körs inte cron. I båda fallen fortsätter du med nästa steg.
1. Mer information om cron. Som användare med `root` behörigheter, ange följande kommando: `$ crontab -u <Magento file system owner name> -l`. Exempel: i CentOS `$ crontab -u magento_user -l`. Om ingen crontab har konfigurerats för användaren visas följande meddelande:    `no crontab for magento_user`. På din crontab ser du följande:
   * Vilken PHP-binär du använder (i vissa fall har du fler än en)
   * Vilka Adobe Commerce-baserade skript du kör (särskilt sökvägarna till dessa skript)
   * Var dina krongloggar finns

   Se något av följande avsnitt för en lösning på ditt problem.

## Lösning: crontab har inte konfigurerats {#solution-crontab-not-set-up}

Information om hur du kontrollerar att dina cron-jobb är korrekt konfigurerade finns i [Ställ in cron-jobb](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron) i vår dokumentation för utvecklare.

## Lösning: Kron körs från felaktig PHP-binär {#solution-cron-running-from-incorrect-php-binary}

Om ditt cron-jobb använder en annan PHP-binärfil än webbserverplugin-programmet kan PHP-inställningsfel visas. Du löser problemet genom att ange identiska PHP-inställningar för både PHP-kommandoraden och PHP-webbserverns plugin-program.

Mer information om PHP-inställningar finns i [Nödvändiga PHP-inställningar](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html) i vår dokumentation för utvecklare.

## Lösning: cron running with errors {#solution-cron-running-with-errors}

Prova att köra varje kommando manuellt eftersom kommandot kan visa praktiska felmeddelanden. Se [Ställ in cron-jobb](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron) i vår dokumentation för utvecklare.

>[!NOTE]
>
>Du måste köra cron åtminstone *två* för att jobbet ska köras. Första gången du ställer jobben i kö är det andra gången du kör jobben.
