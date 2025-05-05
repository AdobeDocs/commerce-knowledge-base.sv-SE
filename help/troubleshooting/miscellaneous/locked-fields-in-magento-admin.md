---
title: Låsta (nedtonade) fält i Commerce Admin
description: Den här artikeln innehåller en lösning för när du inte kan ändra fält i Commerce Admin.
exl-id: 5fe0967a-4241-440b-bb0d-429fa5644bbc
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Låsta (nedtonade) fält i Commerce Admin

Den här artikeln innehåller en lösning för när du inte kan ändra låsta (nedtonade) fält i Commerce Admin.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.3.x, 2.4.x
* Adobe Commerce om molninfrastruktur 2.3.x, 2.4.x

## Problem

När du har sparat en ändring i konfigurationen till `app/etc/env.php` eller `app/etc/config.php` kan du inte ändra inställningen i Admin.

<u>Steg som ska återskapas</u>:

Obs! Detta är ett exempel - problemet kan påverka alla konfigurationer som har sparats.

1. Handlaren sparar sina autentiseringsuppgifter för leveransmetoder med följande kommando i terminalen: `./vendor/bin/ece-tools config:dump`. Detta sparar autentiseringsuppgifterna i filen `app/etc/env.php`.
1. Handlaren försöker sedan ändra inloggningsuppgifterna senare.

<u>Förväntade resultat</u>:

Handlaren kan ange värdena i inställningarna för fältet Admin och spara dem.

<u>Faktiska resultat</u>:

Fälten i Admin är låsta eller så kan värdena ändras men de sparas inte i Admin.

## Orsak

När konfigurationen sparas i `env.php` eller `config.php` kan du inte ändra inställningen i Admin. Om du vill tillåta redigering av inställningen måste du ta bort konfigurationen från `env.php` eller `config.php`.

## Lösning

Kontrollera att konfigurationen inte har sparats i `app/etc/env.php` eller `app/etc/config.php`. Om den har sparats gör du så här:

* `config.php` - Ta bort inställningen och distribuera den sedan igen.
* `env.php` - Ändra detta direkt på servern och ta bort inställningen. Kör sedan `bin/magento app:config:import`.

## Relaterad läsning

* [Exportera konfigurationen](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/cli/configuration-management/export-configuration) i utvecklardokumentationen.
* [Ange konfigurationsvärden](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values) i utvecklardokumentationen.
* [Adobe Commerce i molninfrastruktur: minska driftsättningsdriftsavbrott med Configuration Management](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) i vår kunskapsbas för support.
