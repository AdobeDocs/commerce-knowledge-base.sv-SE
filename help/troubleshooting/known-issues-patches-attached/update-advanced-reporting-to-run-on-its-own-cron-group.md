---
title: Uppdatera avancerad rapportering för att köras på en egen kreditgrupp
description: Den här artikeln innehåller en patch för det kända problemet för Adobe Commerce i molninfrastruktur 2.3.0 där Advanced Reporting inte visar några data. Detta beror på att det avancerade rapporteringsjobbet "analytics_collect_data" inte körs enligt schemat. I den här artikeln finns en patch som skapar en seriegrupp för Advanced Reporting cron "analytics".
exl-id: 8aff9e2b-d9be-4136-975b-05963e23f55c
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Uppdatera avancerad rapportering för att köras på en egen kreditgrupp

Den här artikeln innehåller en patch för det kända problemet för Adobe Commerce i molninfrastruktur 2.3.0 där Advanced Reporting inte visar några data. Detta beror på att det avancerade rapporteringsjobbet `analytics_collect_data` inte körs enligt schemat. I den här artikeln finns en korrigering som skapar en avancerad rapportcron-grupp `analytics`.

## Problem

Inga data har lästs in i modulen Avancerad rapportering.

## Lappa

Korrigeringen är kopplad till den här artikeln. Korrigeringen flyttar de `analytics` kroniska jobbuppgifterna från standardgruppen till `analytics`.

Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[MDVA-19640\_EE\_2.3.0\_COMPOSER\_v1.patch](assets/MDVA-19640_EE_2.3.0_COMPOSER_v1.patch.zip)

Kör följande SQL-fråga när korrigeringen har tillämpats. Frågan måste köras för att poster i tabellen `cron_schedule` ska kunna ändras.

```
UPDATE core_config_data
SET `path` = REPLACE(path, "crontab/default/jobs/analytics", "crontab/analytics/jobs/analytics")
WHERE `path` LIKE "crontab/default/jobs/analytics%";
```

### Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för

* Adobe Commerce om molninfrastruktur 2.3.0

Korrigeringen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce: 2.2.2-2.2.10, 2.3.0-2.3.2 och 2.3.2-p2 och 2.3.3 för Adobe Commerce lokalt och Adobe Commerce i molninfrastrukturen

## Så här sätter du på plåstret

Mer information finns i [Använda en dispositionsruta från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## Bifogade filer
