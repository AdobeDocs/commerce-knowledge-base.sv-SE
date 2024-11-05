---
title: '[!DNL Cron] aktiviteter låser aktiviteter från andra grupper'
description: I den här artikeln finns en lösning på problemet med molninfrastruktur i Adobe Commerce som rör vissa  [!DNL cron] jobb som är igång eller som blockerar andra [!DNL cron] jobb.
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# [!DNL Cron] uppgifter låser uppgifter från andra grupper

Den här artikeln innehåller en lösning för Adobe Commerce om molninfrastruktursproblem som rör vissa [!DNL cron]-jobb som är under lång tid och som blockerar andra [!DNL cron]-jobb.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur Pro planarkitektur
* Inbyggt tidigare än maj 2019

## Problem

Om du har komplexa [!DNL cron]-uppgifter (långkörda uppgifter) i Adobe Commerce för molnet kan de låsa andra uppgifter för körning. Indexerarens uppgift indexerar till exempel om ogiltiga indexerare. Det kan ta några timmar att slutföra och det låser andra standardjobb för [!DNL cron], som att skicka e-post, generera webbplatskartor, kundmeddelanden och andra anpassade uppgifter.

<u>Symtomen</u>:

Processerna som körs av [!DNL cron] jobb utförs inte. Produktuppdateringar gäller t.ex. inte timmar eller så rapporterar kunderna att de inte får några e-postmeddelanden.

När du öppnar databastabellen `cron_schedule` ser du jobben med statusen `missed`.

## Orsak

Tidigare användes Jenkins-servern i vår molnmiljö för att köra [!DNL cron] jobb. Jenkins kör bara en instans av ett jobb åt gången. Därför körs bara en `bin/magento cron:run`-process åt gången.

## Lösning

1. Kontakta [Adobe Commerce support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om du vill att självhanterade [!DNL crons] ska aktiveras.
1. Redigera filen `.magento.app.yaml` i rotkatalogen för koden för Adobe Commerce i grenen [!DNL Git]. Lägg till följande:

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. Spara filen och skicka uppdateringar till miljö för förproduktion och produktion (på samma sätt som för integreringsmiljöer).

>[!NOTE]
>
>Det finns ingen anledning att överföra gamla [!DNL cron]-konfigurationer där det finns flera `cron:run` till det nya [!DNL cron]-schemat. Den vanliga `cron:run`-aktiviteten, som lagts till enligt ovan, räcker. Men du måste överföra dina anpassade jobb om du hade några.

### Kontrollera om du har självhanterade [!DNL cron] aktiverat (endast för molnPro Staging and Production)

Om du vill kontrollera om den självhanterade [!DNL cron] är aktiverad kör du kommandot `crontab -l` och observerar resultatet:

* Självhanterade [!DNL cron] är aktiverade om du kan se aktiviteterna, som följande:

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* Den självhanterade [!DNL cron] är inte aktiverad om du inte kan se aktiviteterna och få felmeddelandet *&quot;du får inte använda det här programmet&quot;*.

>[!NOTE]
>
>Det kommando som anges ovan för att kontrollera om självhanterade [!DNL cron] är aktiverat gäller inte för en Starter-plan eller i utvecklings-/integreringsmiljön.

## Relaterad läsning

* [Konfigurera [!DNL cron] jobb](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) i utvecklardokumentationen
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
