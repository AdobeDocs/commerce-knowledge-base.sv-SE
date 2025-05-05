---
title: Problem med beredskapskontroll av kron
description: 'Den här artikeln innehåller lösningar på problem med viktig beredskap. Följande är symtom på kronproblem:'
exl-id: 1f2cee2c-98ad-4cf5-af16-d736fced2a15
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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
Om du vill se felet kan du behöva klicka på **Systemmeddelanden** högst upp i fönstret enligt följande:
  ![compman_sys-messages.png](assets/compman_sys-messages.png)

## Kontrollera din befintliga crontab {#check-your-existing-crontab}

I det här avsnittet beskrivs hur du ser om cron körs och hur du kontrollerar om det är korrekt konfigurerat.

Så här kontrollerar du om din crontab är inställd:

1. Logga in på din Commerce-server som, eller växla till, ägare av [Magento-filsystemet](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/prerequisites/file-system/overview).
1. Kontrollera om följande fil finns: `$ ls -al <magento_root>/var/.setup_cronjob_status`. Om filen finns har cron körts tidigare. Om filen *inte* finns har du inte installerat Adobe Commerce än eller så körs inte cron. I båda fallen fortsätter du med nästa steg.
1. Mer information om cron. Som användare med `root`-behörighet anger du följande kommando: `$ crontab -u <Magento file system owner name> -l`. Exempel: i CentOS `$ crontab -u magento_user -l`. Om ingen crontab har konfigurerats för användaren visas följande meddelande:    `no crontab for magento_user`. På din crontab ser du följande:
   * Vilken PHP-binär du använder (i vissa fall har du fler än en)
   * Vilka Adobe Commerce-baserade skript du kör (särskilt sökvägarna till dessa skript)
   * Var dina krongloggar finns

   Se något av följande avsnitt för en lösning på ditt problem.

## Lösning: crontab har inte konfigurerats {#solution-crontab-not-set-up}

Information om hur du kontrollerar att dina cron-jobb är korrekt konfigurerade finns i [Konfigurera cron-jobb](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/next-steps/configuration) i utvecklardokumentationen.

## Lösning: Kron körs från felaktig PHP-binär {#solution-cron-running-from-incorrect-php-binary}

Om ditt cron-jobb använder en annan PHP-binärfil än webbserverplugin-programmet kan PHP-inställningsfel visas. Du löser problemet genom att ange identiska PHP-inställningar för både PHP-kommandoraden och PHP-webbserverns plugin-program.

Mer information om PHP-inställningar finns i [Nödvändiga PHP-inställningar](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/prerequisites/php-settings) i utvecklardokumentationen.

## Lösning: cron running with errors {#solution-cron-running-with-errors}

Prova att köra varje kommando manuellt eftersom kommandot kan visa praktiska felmeddelanden. Se [Konfigurera kronijobb](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/next-steps/configuration) i utvecklardokumentationen.

>[!NOTE]
>
>Du måste köra minst *två gånger* för att jobbet ska kunna köras. Första gången du ställer jobben i kö är det andra gången som jobben ska köras.
