---
title: Kravuppgifter låser uppgifter från andra grupper
description: Den här artikeln innehåller en lösning för Adobe Commerce om molninfrastrukturproblem i samband med vissa kron-jobb som är under lång tid och som blockerar andra kron-jobb.
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
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

<u>Symtom</u>:

Processerna som utförs av cron-jobb utförs inte. Produktuppdateringar gäller t.ex. inte timmar eller så rapporterar kunderna att de inte får några e-postmeddelanden.

När du öppnar `cron_schedule` databastabell, du ser jobben med `missed` status.

## Orsak

Tidigare användes Jenkins-servern i vår molnmiljö för att köra cron-jobb. Jenkins kör bara en instans i taget och det blir därför bara en i taget `bin/magento cron:run` processer som körs i taget.

## Lösning

1. Kontakt [Adobe Commerce support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) att ha självhanterade kroner aktiverade.
1. Redigera `.magento.app.yaml` i rotkatalogen för koden för Adobe Commerce i Git-grenen. Lägg till följande:

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. Spara filen och skicka uppdateringar till miljö för förproduktion och produktion (på samma sätt som för integreringsmiljöer).

>[!NOTE]
>
>Du behöver inte överföra gamla cron-konfigurationer där flera `cron:run` är närvarande i det nya kronschemat; den `cron:run` uppgiften som lagts till enligt ovan räcker. Men du måste överföra dina anpassade jobb om du hade några.

### Kontrollera om du har självhanterade kron aktiverat (endast för Cloud Pro Staging and Production)

Kör `crontab -l` och observera resultatet:

* Självhanterade kroner är aktiverade om du kan se åtgärderna, som följande:

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* Den självhanterade kron är inte aktiverad om du inte kan se aktiviteterna och få *&quot;du får inte använda det här programmet&quot;* felmeddelande.

>[!NOTE]
>
>Det kommando som anges ovan för att kontrollera om självhanterade kron är aktiverat gäller inte för en Starter-plan eller i utvecklings-/integreringsmiljön.

## Relaterad läsning

* [Ställ in cron-jobb](https://devdocs.magento.com/guides/v2.3/cloud/configure/setup-cron-jobs.html) i vår utvecklardokumentation
