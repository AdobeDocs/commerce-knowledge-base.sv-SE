---
title: Konfigurationsfilen saknas eller har ändrats
description: Lös problemet med saknade eller ändrade konfigurationsfiler för Adobe Commerce.
exl-id: d80bf981-8ba6-4357-a841-57bf5d3f2a3f
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# Konfigurationsfilen saknas eller har ändrats

I den här artikeln beskrivs hur du löser ett problem där konfigurationsfilerna har ändrats eller saknas.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur, alla versioner

## Problem

Konfigurationsfilerna `config.php` och/eller `env.php` ändrades felaktigt eller saknas.

## Lösning

Distributionsprocessen skapar en säkerhetskopieringsfil för varje konfigurationsfil:

* `app/etc/config.php.bak` - innehåller systemspecifika inställningar och genereras automatiskt under bygget om det inte finns
* `app/etc/env.php.bak` - innehåller känsliga konfigurationsdata

Du kan återställa dem med ECE-verktygen `backup:restore`.

BAK-filerna är en produkt i distributionsprocessen. Om du ändrar en konfigurationsfil manuellt efter distributionen återspeglas ändringarna inte i de befintliga BAK-filerna.

Så här återställer du konfigurationsfilerna:

1. Logga in på fjärrdatabasen med [SSH](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh).
1. Visa en lista över tillgängliga säkerhetskopieringsfiler.

   ```
   ./vendor/bin/ece-tools backup:list
   ```

   ```
   The list of backup files:
   app/etc/env.php
   app/etc/config.php
   ```

1. Återställ konfigurationsfilerna.

   ```
   ./vendor/bin/ece-tools backup:restore
   ```

   Du får en lista över befintliga konfigurationsfiler som påverkas av återställningen.

   ```
   app/etc/env.php file exists! If you want to rewrite existed files use --force
   app/etc/config.php file exists! If you want to rewrite existed files use --force
   ```

1. Använd alternativet `--force` om du vill skriva över alla filer.

   ```
   ./vendor/bin/ece-tools backup:restore --force
   ```

   ```
   Command backup:restore with option --force will rewrite your existed files. Do you want to continue [y/N]?y
   Backup file app/etc/env.php was restored.
   Backup file app/etc/config.php was restored.
   ```

1. Du kan också återställa en viss konfigurationsfil.

   ```
   ./vendor/bin/ece-tools backup:restore --force --file=app/etc/config.php
   ```

   ```
   Command backup:restore with option --force will rewrite your existed files. Do you want to continue [y/N]?y
   Backup file app/etc/config.php was restored.
   ```
