---
title: Så här kontrollerar du varför [!DNL cron] inaktiverades
description: I den här artikeln finns felsökningslösningar för problem med kron i Adobe Commerce för molninfrastrukturprodukter.
feature: Configuration
role: Developer
exl-id: d4d4a28d-3afa-4379-afc1-bc6250717784
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Kontrollera varför [!DNL cron] inaktiverades

I den här artikeln finns felsökningslösningar för problem med [!DNL cron] i Adobe Commerce för molninfrastrukturprodukter.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur, alla versioner

## Problem

## Följande är symtom på [!DNL cron] problem:

Du har lagt märke till att din [!DNL cron] inte kördes.
Du kan till exempel se följande rader i filen `app/etc/env.php`:

```'cron' =>
  array (
    'enabled' => 0
  ),
```

En tom array skulle innebära att [!DNL cron] är **aktiverad**:

```'cron' =>
  array (
  ),
```

## Orsaker

Det finns flera orsaker till varför [!DNL cron] inte är aktiv just nu:

1. [!DNL cron] inaktiverades på grund av missade [!DNL OpCache]-inställningar.
1. Infrastrukturteamet inaktiverade din [!DNL cron] eftersom det gjorde att din plats presterade dåligt/gick ned.
1. [!DNL cron] återaktiverades inte eftersom distributionen misslyckades.

Se något av följande avsnitt för en lösning på ditt problem.

## Lösningar

### Lösning för missade [!DNL OpCache]-inställningar {#solution-missed-opcache-settings}

Se [[!DNL Cron] stoppad på grund av felkonfigurerade eller saknade [!DNL OpCache] inställningar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/crons-blocked-running-missing-opache-settings) i Commerce kunskapsbas.

### Lösning för inaktiverad av infrastrukturteamet {#solution-disabled-by-infrastructure-team}

1. Kontrollera dina tidigare supportärenden där sajten var nere eller inte svarade.
1. Kontrollera sedan om infrastrukturteamet har angett att de har inaktiverat det.
1. Kontrollera att du har åtgärdat de problem/problem som infrastrukturteamet har tagit upp.
1. Skicka en [supportförfrågan](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) om du behöver ytterligare hjälp för att kunna återaktivera [!DNL cron] och förklara hur du har åtgärdat de problem som infrastrukturteamet har angett.

### Distributionslösningen misslyckades {#solution-deployment-failed}

Kontrollera distributionsloggarna:

* [Visa och hantera loggar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations) i vår Commerce on Cloud Infrastructure Guide.
* [Kontrollerar distributionsloggen om molngränssnittet har *`log snipped`* error](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error) i Commerce kunskapsbas.

1. Om distributionen misslyckades under steget `setup:upgrade` kommer [!DNL cron] inte att ha återaktiverats.
Du kan till exempel se den här raden i distributionsloggen:

   ```The command "/bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade --keep-generated --ansi --no-interaction  | tee -a /app/$<project_id>/var/log/install_upgrade.log"" failed. Cache types config flushed successfully```

1. Annars kan distributionen ha misslyckats under någon annan fas. Kontrollera distributionsloggen och se till att båda raderna visas (exempel nedan). Om du inte ser båda raderna som liknar detta i loggen innebär det att [!DNL cron] inte återaktiverades:

   ```  [2024-03-06T10:55:39.345564+00:00] INFO: Disable cron```<br>
...<br>
   ```  [2024-02-07T10:50:09.579005+00:00] INFO: Enable cron```

**Skicka en [supportförfrågan](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) om du behöver mer hjälp.**
