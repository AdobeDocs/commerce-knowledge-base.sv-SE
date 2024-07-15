---
title: Felsök kron
description: I den här artikeln finns felsökningslösningar för problem med kron i Adobe Commerce lokala produkter.
exl-id: e69a4fb3-731b-449e-a815-c33cd2faa567
feature: Configuration
role: Developer
source-git-commit: b6a79bcff3d757d40e7070182d8853a37960a782
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Felsök kron

I den här artikeln finns felsökningslösningar för problem med kron i Adobe Commerce lokala produkter.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Problem

## Följande är symtom på kronproblem:

* Uppdateringen eller uppgraderingen körs aldrig. Den är fortfarande i läget `pending`.
* Ett felmeddelande om [PHP](https://glossary.magento.com/php)-inställningen `$HTTP_RAW_POST_DATA` visas även om den är korrekt inställd.
* Kronberedskapskontrollen misslyckas. Möjliga fel kan vara icke-skrivbara sökvägar och cron inte konfigurerade. Ett exempel följer:

  ![upgr-tshot-no-cron2.png](assets/upgr-tshoot-no-cron2.png)

* PHP-beredskapskontrollen visar inte PHP-versionen som på bilden nedan.

  ![Screen_Shot_2019-08-29_at_1.36.08_PM.png](assets/Screen_Shot_2019-08-29_at_1.36.08_PM.png)

* Följande fel visas i Commerce Admin:

  ![compman-cron-not-running.png](assets/compman-cron-not-running.png)

Om du vill se felet kan du behöva klicka på **Systemmeddelanden** högst upp i fönstret enligt följande:

![compman_sys-messages.png](assets/compman_sys-messages.png)

## Undersök för att hitta orsaken {#check-your-existing-crontab}

I det här avsnittet beskrivs hur du ser om cron körs och hur du kontrollerar om det är korrekt konfigurerat.

Så här kontrollerar du om din crontab är inställd:

1. Logga in på Magento-servern som, eller växla till, ägare av [Magento-filsystemet](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html).
1. Kontrollera om följande fil finns:    `bash    ls -al <magento_root>/var/.setup_cronjob_status`. Om filen finns har cron körts tidigare. Om filen *inte* finns, har du inte installerat Magento än eller så körs inte cron. I båda fallen fortsätter du med nästa steg.
1. Mer information om cron. Som användare med `root`-behörighet anger du följande kommando:    `bash    crontab -u <Magento file system owner name> -l`. Exempel: i CentOS `bash    crontab -u magento_user -l`.  Om ingen crontab har konfigurerats för användaren visas följande meddelande:    `terminal    no crontab for magento_user`. På din crontab ser du följande:

   * Vilken PHP-binär du använder (i vissa fall har du fler än en)
   * Vilka Magento-baserade skript du kör (särskilt sökvägarna till dessa skript)
   * Var dina krongloggar finns

Se något av följande avsnitt för en lösning på ditt problem.

## Lösningar

### Lösning för crontab konfigureras inte {#solution-crontab-not-set-up}

Se [Konfigurera cron-jobb](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron) för att kontrollera att dina cron-jobb är korrekt konfigurerade.

### Lösning för cron som körs från felaktig PHP-binär {#solution-cron-running-from-incorrect-php-binary}

Om ditt cron-jobb använder en annan PHP-binärfil än webbserverplugin-programmet kan PHP-inställningsfel visas. Du löser problemet genom att ange identiska PHP-inställningar för både PHP-kommandoraden och PHP-webbserverns plugin-program.

Mer information om PHP-inställningar finns i [Nödvändiga PHP-inställningar](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html) i utvecklardokumentationen.

### Lösning för cron som körs med fel {#solution-cron-running-with-errors}

Prova att köra varje kommando manuellt eftersom kommandot kan visa praktiska felmeddelanden. Se [Konfigurera cron-jobb](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron).

>[!NOTE]
>
>Du måste köra minst *två gånger* för att jobbet ska kunna köras. Första gången du ställer jobben i kö är det andra gången som jobben ska köras.
