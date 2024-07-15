---
title: Läs replikeringsproblem i Adobe Commerce Cloud 2.4.6 med MariaDB 10.6
description: I den här artikeln beskrivs hur du felsöker Läs repliker-problem i Adobe Commerce Cloud 2.4.6 med MariaDB 10.6.
feature: Configuration
role: Developer,Admin
exl-id: b7af1cc3-93ff-40c5-8959-076cedddb56d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Läs replikeringsproblem i Adobe Commerce Cloud 2.4.6 med MariaDB 10.6

Den här artikeln innehåller lösningar på oväntat beteende när du använder Läs repliker i Adobe Commerce Cloud 2.4.6 med MariaDB 10.6+.

## Berörda produkter och versioner

* MariaDB 10.6+
* Adobe Commerce i molninfrastruktur 2.4.6

## Problem

Icke-kritiska läsningar visar felaktig information.

## Orsak

Konfigurationen `slave_parallel_mode` för databasen ändrades som standard till *optimistics* när värdet ska vara *conservative*, och värdet `synchronous_replication` i Ece-Tools är som standard *true* när värdet ska vara *false*.

## Lösning

1. Kontrollera att parametern `slave_parallel_mode` är inställd på *konservativ* (du måste [höja upp en supportbiljett](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) om värdet inte visas som *konservativ*). Kör följande kommando för att kontrollera:

   ```
    MariaDB [main]> show variables like 'slave_parallel_mode';
    +---------------------+--------------+
    | Variable_name       | Value        |
    +---------------------+--------------+
    | slave_parallel_mode | conservative |
    +---------------------+--------------+
    1 row in set (0.001 sec)
   ```

1. Uppdatera databaskonfigurationer för `.magento.env.yaml` till:

   ```yaml
       DATABASE_CONFIGURATION:
        _merge: true
           slave_connection:
               default:
                   synchronous_replication: false
   ```



Anvisningar om hur du uppdaterar databaskonfigurationen finns i [DATABASE_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#database_configuration) i avsnittet Distribuera variabler i Commerce on Cloud Infrastructure Guide.


## Relaterad läsning

* [Konfigurera miljövariabler för distribution](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) i Commerce i molninfrastrukturguiden.
* [Bästa tillvägagångssätt för databaskonfiguration](/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) i implementeringens spelningsbok.
