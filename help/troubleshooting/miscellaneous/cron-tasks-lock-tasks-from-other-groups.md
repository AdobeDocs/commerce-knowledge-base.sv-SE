---
title: Kravuppgifter låser uppgifter från andra grupper
description: Den här artikeln innehåller en lösning för Adobe Commerce om molninfrastrukturproblem i samband med vissa kron-jobb som är under lång tid och som blockerar andra kron-jobb.
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: faa80e8233438fc15781341b3a9d5325269d6d20
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Kravuppgifter låser uppgifter från andra grupper

Den här artikeln innehåller en lösning för Adobe Commerce om molninfrastrukturproblem i samband med vissa kron-jobb som är under lång tid och som blockerar andra kron-jobb.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur Pro planarkitektur
* Inbyggt tidigare än maj 2019

## Problem

När du har komplexa kron-uppgifter (långkörda uppgifter) i Adobe Commerce för molnet kan de låsa andra uppgifter för körning. Indexerarens uppgift indexerar till exempel om ogiltiga indexerare. Det kan ta några timmar att slutföra och låser andra standardcron-jobb som att skicka e-post, generera webbplatskartor, kundmeddelanden och andra anpassade uppgifter.

<u>Symtomen</u>:

Processerna som utförs av cron-jobb utförs inte. Produktuppdateringar gäller t.ex. inte timmar eller så rapporterar kunderna att de inte får några e-postmeddelanden.

När du öppnar databastabellen `cron_schedule` ser du jobben med statusen `missed`.

## Orsak

Tidigare användes Jenkins-servern i vår molnmiljö för att köra cron-jobb. Jenkins kör bara en instans av ett jobb åt gången. Därför körs bara en `bin/magento cron:run`-process åt gången.

## Lösning

1. Kontakta [Adobe Commerce support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om du vill att självhanterade kroner ska vara aktiverade.
1. Redigera filen `.magento.app.yaml` i rotkatalogen för Adobe Commerce i Git-grenen. Lägg till följande:

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. Spara filen och skicka uppdateringar till miljö för förproduktion och produktion (på samma sätt som för integreringsmiljöer).

>[!NOTE]
>
>Det finns ingen anledning att överföra gamla cron-konfigurationer där det finns flera `cron:run` till det nya cron-schemat. Den vanliga `cron:run`-aktiviteten, som lagts till enligt ovan, räcker. Men du måste överföra dina anpassade jobb om du hade några.

### Kontrollera om du har självhanterade kron aktiverat (endast för Cloud Pro Staging and Production)

Om du vill kontrollera om den självhanterade kronen är aktiverad kör du kommandot `crontab -l` och observerar resultatet:

* Självhanterade kroner är aktiverade om du kan se åtgärderna, som följande:

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* Den självhanterade kron är inte aktiverad om du inte kan se aktiviteterna och få felmeddelandet *&quot;du får inte använda det här programmet&quot;*.

>[!NOTE]
>
>Det kommando som anges ovan för att kontrollera om självhanterade kron är aktiverat gäller inte för en Starter-plan eller i utvecklings-/integreringsmiljön.

## Relaterad läsning

* [Konfigurera cron-jobb](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) i utvecklardokumentationen.
