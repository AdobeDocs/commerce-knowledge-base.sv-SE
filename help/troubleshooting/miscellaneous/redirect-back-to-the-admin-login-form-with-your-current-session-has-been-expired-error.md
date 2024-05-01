---
title: Omdirigera tillbaka till inloggningsformuläret för Commerce Admin med felmeddelandet"Din nuvarande session har gått ut"
description: 'I den här artikeln beskrivs möjliga lösningar på inloggningsproblemet för Commerce Admin, där du omdirigeras tillbaka till inloggningsformuläret med följande felmeddelande: *"Din nuvarande session har gått ut"*. Lösningarna omfattar kontroll av servertidsinställningar och ändring av inställningar för sessionslagring.'
exl-id: 29df2ed2-ff4a-4f1a-bdb7-1160416cda00
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Omdirigera tillbaka till inloggningsformuläret för Commerce Admin med felmeddelandet&quot;Din nuvarande session har gått ut&quot;

I den här artikeln beskrivs möjliga lösningar på inloggningsproblemet för Commerce Admin, där du omdirigeras tillbaka till inloggningsformuläret med följande felmeddelande: *&quot;Din nuvarande session har gått ut&quot;*. Lösningarna omfattar kontroll av servertidsinställningar och ändring av inställningar för sessionslagring.

## Berörda versioner:

Alla Adobe Commerce-versioner och -utgåvor

## Problem

<u>Steg som ska återskapas</u>:

1. Gå till sidan Commerce Admin.
1. Ange dina inloggningsuppgifter och klicka på Logga in.

<u>Förväntat resultat</u>:

Du loggas in på Commerce Admin.

<u>Faktiskt resultat</u>:

Du omdirigeras tillbaka till inloggningsformuläret med följande felmeddelande: *&quot;Din nuvarande session har gått ut&quot;*.

## Orsak

Det kan finnas två möjliga orsaker till problemet:

* ett problem med servertidsinställningarna
* ett problem med sessionslagring

Sök efter lösningar i följande avsnitt.

## Lösning

### Kontrollera om det finns problem med servertidsinställningar

Kontrollera sessionsposten som skapats i `admin_user_session` tabell. Om värdena för `created_at` och/eller `updated_at` är felaktiga kan det bero på ett problem med servertidsinställningarna. Be serversystemadministratören kontrollera detta. Observera att tiden i DB är inställd på UTC som standard.

### Ändra sessionslagring

Försök att ändra sessionslagringen. Använd informationen från [Hitta dina sessionsfiler](https://devdocs.magento.com/guides/v2.3/config-guide/sessions.html) artikel i vår utvecklardokumentation för att ta reda på var din session är lagrad och ändra den genom att redigera `app/etc/env.php` -fil.

Om du till exempel vill börja lagra sessionen i filsystemet ändrar du `'session'` enligt följande:

```php
....
'session' =>
    array (
      'save' => 'files',
),
....
```

Kör `bin/magento app:config:import` för att importera konfigurationsdata.


## Relaterad läsning

* [Importera data från konfigurationsfiler](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-config-mgmt-import.html) i vår utvecklardokumentation
* [Konfigurera Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html) i vår utvecklardokumentation
* [Omdirigera tillbaka till inloggningsformuläret för Commerce Admin med felmeddelandet&quot;Ditt konto är tillfälligt inaktiverat&quot;](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md) i vår kunskapsbas
* [Omdirigera tillbaka till inloggningsformuläret utan fel när du försöker logga in på Commerce Admin](/help/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin.md) i vår kunskapsbas
