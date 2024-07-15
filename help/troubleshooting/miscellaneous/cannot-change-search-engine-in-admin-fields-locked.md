---
title: Det går inte att ändra sökmotorn i "app/etc/env.php"
description: Den här artikeln innehåller en lösning på problemet där du försöker byta sökmotor i Commerce Admin, men fälten är låsta.
exl-id: 61006ce7-34f9-4e4d-a197-f3d627dd277f
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Det går inte att ändra sökmotor i `app/etc/env.php`

Den här artikeln innehåller en lösning på problemet där du försöker ta bort sökmotorkonfigurationen från filen `app/etc/env.php`, men efter omdistributionen återställs konfigurationen till den tidigare inställningen eller ändras till [!DNL OpenSearch] som standard.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur, [alla versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Du försöker ändra sökmotorn i Commerce Admin, men fälten är låsta.

## Orsak

Sökmotorkonfigurationen är låst i filen `app/etc/env.php` eller så definieras sökmotorn uttryckligen i filen `.magento.env.yaml`.

## Lösning

1. Kontrollera filen `.magento.env.yaml` under distributionsfasen och se om variabeln `SEARCH_CONFIGURATION` har konfigurerats. Exempel:

   ```yaml
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     ...
   <VARIABLE X>
   ```

1. Finns variabeln `SEARCH_CONFIGURATION`? Om den inte finns är sökmotorkonfigurationen som standard låst till [!DNL OpenSearch]. Om du vill ändra konfigurationen måste du lägga till variabeln i filen `.magento.env.yaml` med rätt värde för sökmotorn. Om variabeln `SEARCH_CONFIGURATION` finns med och du vill ändra motorn ersätter du det befintliga värdet för motorn i `.magento.env.yaml`. Möjliga/kända värden: [!DNL opensearch], [!DNL livesearch], [!DNL elasticsuite], [!DNL amasty_elastic] och [!DNL amasty_elastic_opensearch].
1. Distribuera om instansen.
1. Sökmotorfältet i Admin förblir låst, men det bör uppdateras med det värde du har angett.

## Relaterad läsning

* [Låsta fält i Commerce Admin](/help/troubleshooting/miscellaneous/locked-fields-in-magento-admin.md) i Commerce i molninfrastrukturguiden.
