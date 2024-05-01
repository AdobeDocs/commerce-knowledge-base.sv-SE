---
title: Låsta fält i Commerce Admin
description: Den här artikeln innehåller en lösning för när du inte kan ändra fält i Commerce Admin.
exl-id: 5fe0967a-4241-440b-bb0d-429fa5644bbc
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Låsta fält i Commerce Admin

Den här artikeln innehåller en lösning för när du inte kan ändra fält i Commerce Admin.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.3.x, 2.4.x
* Adobe Commerce om molninfrastruktur 2.3.x, 2.4.x

## Problem

När du har sparat en ändring i konfigurationen till `app/etc/env.php` eller `app/etc/config.php`kan du inte ändra inställningen i Admin.

<u>Steg som ska återskapas</u>:

Obs! Detta är ett exempel - problemet kan påverka alla konfigurationer som har sparats.

1. Handlaren sparar sina autentiseringsuppgifter för leveransmetoder med följande kommando i terminalen: `./vendor/bin/ece-tools config:dump`. Då sparas inloggningsuppgifterna i `app/etc/env.php` -fil.
1. Handlaren försöker sedan ändra inloggningsuppgifterna senare.

<u>Förväntade resultat</u>:

Handlaren kan ange värdena i inställningarna för fältet Admin och spara dem.

<u>Faktiska resultat</u>:

Fälten i Admin är låsta eller så kan värdena ändras men de sparas inte i Admin.

## Orsak

När konfigurationen sparas i `env.php` eller `config.php`kan du inte ändra inställningen i Admin. Om du vill tillåta redigering av inställningen måste du ta bort konfigurationen från `env.php` eller `config.php`.

## Lösning

Kontrollera att konfigurationen inte har sparats i `app/etc/env.php` eller `app/etc/config.php`. Om den har sparats gör du så här:

* `config.php` - Ta bort inställningen och återdistribuera den.
* `env.php` - Ändra detta direkt på servern och ta bort inställningen. Kör sedan `bin/magento app:config:import`.

## Relaterad läsning

* [Exportera konfigurationen](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-config-mgmt-export.html#sensitive-or-system-specific-settings) i vår dokumentation för utvecklare.
* [Ange konfigurationsvärden](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-config-mgmt-set.html#config-cli-config-set) i vår dokumentation för utvecklare.
* [Adobe Commerce i molninfrastruktur: minska driftsättningsdriftsavbrott med Configuration Management](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) i vår kunskapsbas för support.
