---
title: Omdistributionen av miljön misslyckades eller MySQL-servern har försvunnit
description: I den här artikeln finns en lösning för Adobe Commerce-problem (alla distributionsmetoder) där minnesbrist för MySQL orsakar problem med fast distribution eller databasanslutning.
exl-id: 2086b45a-0bfe-45cc-bef9-1b6f09ddb70a
feature: Deploy, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Omdistributionen av miljön misslyckades eller MySQL-servern har försvunnit

I den här artikeln finns en lösning för Adobe Commerce-problem (alla distributionsmetoder) där minnesbrist för MySQL orsakar problem med fast distribution eller databasanslutning.

## Berörda produkter och versioner

* Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur (alla versioner)

## Problem

* Distributionsprocessen misslyckas med följande fel i distributionsloggen (kommandorad och gränssnittslogg): ```bash    Re-deploying environment abcdefghijklm-master-7rqtwti         E: Environment redeployment failed    ```
* Adobe Commerce svarar med 503-fel och följande felmeddelande visas i programloggarna:    ```bash    SQLSTATE[HY000] [2006] MySQL server has gone away    ```    och följande fel visas när du ansluter till en MySQL-server:    ```bash    ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0 "Internal error/check (Not system error)"    ```

## Orsak

Den troligaste orsaken till problemen är att det tilldelade utrymmet i MySQL-databasen är för lågt. Om du vill vara säker på att så är fallet kontrollerar du det tillgängliga utrymmet för MySQL enligt beskrivningen ytterligare.

### Kontrollera om det finns tillräckligt med utrymme för MySQL

För alla arkitekturmiljöer för Starter-planer för molninfrastruktur och [Integreringsmiljö](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) för Adobe Commerce-planarkitekturen för molninfrastruktur Pro [SSH till miljön](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) och kör kommandot:

```bash
magento-cloud db:size
```

[SSH till miljön](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) och kör `df -h` för den förproduktion eller produktionsmiljö som Pro-arkitekturen omfattar.   `| grep mysql` . Resultatet kommer att se ut ungefär så här:

```bash
sxpe7gigd5ok2@i-00baa9e24f31dba41:~$ df -h | grep mysql
/dev/xvdj                            40G  7.4G   32G  19% /data/mysql
```

## Lösning

### För att lösa problemet måste du tilldela mer utrymme till MySQL.

För alla integreringsmiljöer för Starter-arkitekturen och Pro-arkitekturen görs detta i filen `.magento/services.yaml` genom att parametern `mysql: disk:` ökas. Exempel:

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

Se artikeln [Konfigurera MySQL-tjänsten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html) för referens.

Om du vill göra de här ändringarna för mellanlagrings- eller produktionsmiljön i Pro-arkitekturen måste du skapa en [supportanmälan](https://support.magento.com). Men vanligtvis behöver du inte hantera detta på Staging/Production av Pro-arkitekturen eftersom Adobe Commerce övervakar parametrarna åt dig och varnar dig och/eller vidtar åtgärder enligt kontraktet.

### Använda ändringarna

När du har ändrat filen `.magento/services.yaml` måste du implementera och överföra dina ändringar för att de ska tillämpas. Tryckningen kommer att utlösa distributionsprocessen.
