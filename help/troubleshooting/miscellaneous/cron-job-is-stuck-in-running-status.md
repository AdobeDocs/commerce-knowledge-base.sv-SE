---
title: "[!DNL Cron]-jobbet har fastnat i **löpande**-status"
description: Den här artikeln innehåller lösningar för när Adobe Commerce [!DNL cron] jobb inte har slutförts och kvarstår i körningsstatus, vilket förhindrar att andra [!DNL cron] jobb körs. Detta kan inträffa av flera orsaker, t.ex. nätverksproblem, programkrascher och problem med omdistribution.
exl-id: 11e01a2b-2fcf-48c2-871c-08f29cd76250
feature: Configuration
role: Developer
source-git-commit: 08a241131453725a86eda5f267a209e6705da2e3
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# Jobbet [!DNL Cron] har fastnat i statusen&quot;kör&quot;

Den här artikeln innehåller lösningar för när Adobe Commerce [!DNL cron]-jobb inte har slutförts och fortfarande har statusen&quot;körs&quot;, vilket förhindrar att andra [!DNL cron]-jobb körs. Detta kan inträffa av flera orsaker, t.ex. nätverksproblem, programkrascher och problem med omdistribution.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur, alla versioner

## Symptom {#symptom}

Symtomen på [!DNL cron] jobb som måste återställas är:

* Ett stort antal jobb visas i kön `cron_schedule`
* Webbplatsprestanda börjar försämras
* Jobb kan inte köras enligt schema

## Lösningar {#solutions}

### Lösning för att stoppa alla [!DNL cron] jobb samtidigt {#solution-stop-all-crons-at-once}

>[!WARNING]
>
>Om du kör det här kommandot utan alternativet `--job-code` återställs *all* [!DNL cron] -jobb, även de som körs för närvarande, så vi rekommenderar att du bara använder det i undantagsfall, till exempel efter att du har verifierat att alla [!DNL cron]-jobb måste återställas. Omdistribution kör som standard det här kommandot för att återställa [!DNL cron] jobb, så att de återställs korrekt efter att miljön har säkerhetskopierats. Undvik att använda den här lösningen när indexerare körs.

För att lösa det här problemet måste du återställa [!DNL cron] jobb med kommandot `cron:unlock`. Det här kommandot ändrar status för jobbet [!DNL cron] i databasen och avslutar jobbet så att andra schemalagda jobb kan fortsätta.

1. Öppna en terminal och använd dina [SSH-nycklar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) för att ansluta till den drabbade miljön.
1. Hämta inloggningsuppgifterna för MySQL-databasen:    ```shell    echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp    ```
1. Anslut till databasen med `mysql`:    ```shell    mysql -hdatabase.internal -uuser -ppassword main    ```
1. Välj `main`-databasen:    ```shell    use main    ```
1. Sök efter alla [!DNL cron] jobb som körs:    ```shell    SELECT * FROM cron_schedule WHERE status = 'running';    ```
1. Kopiera `job_code` för alla jobb som körs längre än vanligt.
1. Använd schema-ID:n från föregående steg för att låsa upp specifika [!DNL cron] jobb:    ```shell    ./vendor/bin/ece-tools cron:unlock --job-code=<job_code_1> [... --job-code=<job_code_x>]    ```

### Lösning för att stoppa en enskild [!DNL cron] {#solution-stop-a-single-cron}

1. Öppna en terminal och använd dina [SSH-nycklar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) för att ansluta till den drabbade miljön.
1. Kontrollera tidskrävande uppgifter med följande kommando:

   ```date; ps aux | grep '[%]CPU\|cron\|magento\|queue' | grep -v 'grep\|cron -f'```

1. I utdata, som i exempelutdata nedan, visas aktuellt datum och en lista över processer. Kolumnen `START` visar starttid eller startdatum för processen:

   ```
   Wed May  8 22:41:31 UTC 2019
   USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
   root       590  0.0  0.0  27528  2768 ?        Ss   Jan15   0:49 /usr/sbin/cron -f
   bxc2qly+ 25855  0.0  0.0  23724  2184 ?        S    20:51   0:00 logger -d -u /run/bxc2qlykqhbqe_stg-cron.sock -p cron.info -s -t cron-bxc2qlykqhbqe_stg-bxc2qlykqhbqe_stg
   bxc2qly+ 25860 57.7  1.3 584220 222692 ?       S    20:51   0:02 php bin/magento cron:run
   bxc2qly+ 25863  0.0  0.0  23724  2472 ?        S    20:51   0:00 logger -d -u /run/bxc2qlykqhbqe-cron.sock -p cron.info -s -t cron-bxc2qlykqhbqe-bxc2qlykqhbqe
   bxc2qly+ 25876 53.0  0.6 475472 111468 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25878 57.0  0.6 475472 112080 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=staging --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25880 50.5  0.6 475472 111312 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=catalog_event --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25882 48.5  0.6 475472 111220 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=consumers --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25884 50.5  0.6 475472 111372 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=ddg_automation --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25890 32.5  0.6 475368 110672 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=staging --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25892 34.5  0.6 475472 110724 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=catalog_event --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25894 31.5  0.6 475368 110136 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=consumers --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25896 29.0  0.6 475320 109876 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=ddg_automation --bootstrap=standaloneProcessStarted=1
   ```

1. Om du ser ett [!DNL cron]-jobb som körs länge, vilket kan vara blockdistributionsprocessen, kan du avsluta processen med kommandot `kill` . Du kan identifiera **process-ID** (hittade kolumnen `PID`) och sedan placera `PID` i kommandot för att avsluta processen.
Kommandot **Avsluta process** är:

   ```kill -9 <PID>```

1. Sedan kan ni omdistribuera, om ni försöker omdistribuera.
