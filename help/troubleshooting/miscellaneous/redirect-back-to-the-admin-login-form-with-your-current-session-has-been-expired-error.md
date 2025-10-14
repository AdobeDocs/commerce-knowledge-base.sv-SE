---
title: Omdirigera tillbaka till inloggningsformuläret [!UICONTROL Commerce Admin] med felet"Din nuvarande session har gått ut"
description: 'I den här artikeln finns möjliga lösningar på inloggningsproblemet [!UICONTROL Commerce Admin], där du omdirigeras tillbaka till inloggningsformuläret med följande felmeddelande: *"Din nuvarande session har gått ut"*. Lösningarna omfattar kontroll av servertidsinställningar och ändring av inställningar för sessionslagring.'
exl-id: 29df2ed2-ff4a-4f1a-bdb7-1160416cda00
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Omdirigera tillbaka till inloggningsformuläret [!UICONTROL Commerce Admin] med felet&quot;Din nuvarande session har gått ut&quot;

Den här artikeln innehåller möjliga lösningar på inloggningsproblemet [!UICONTROL Commerce Admin], där du omdirigeras tillbaka till inloggningsformuläret med följande felmeddelande: *&quot;Din aktuella session har gått ut&quot;*. Lösningarna omfattar kontroll av servertidsinställningar och ändring av inställningar för sessionslagring.

## Berörda versioner:

Alla Adobe Commerce-versioner och -utgåvor

## Problem

<u>Steg som ska återskapas</u>:

1. Gå till sidan **[!UICONTROL Commerce Admin]**.
1. Ange dina autentiseringsuppgifter och klicka på **Logga in**.

<u>Förväntat resultat</u>:

Du loggas in på [!UICONTROL Commerce Admin].

<u>Faktiskt resultat</u>:

Du omdirigeras tillbaka till inloggningsformuläret med följande felmeddelande: *&quot;Din aktuella session har gått ut&quot;*.

## Orsak

Det kan finnas två möjliga orsaker till problemet:

* ett problem med servertidsinställningarna
* ett problem med sessionslagring

Sök efter lösningar i följande avsnitt.

## Lösning

### Kontrollera om det finns problem med servertidsinställningar

Kontrollera sessionsposten som skapats i tabellen `admin_user_session`. Om värdena för `created_at` och/eller `updated_at` är felaktiga kan det bero på ett problem med servertidsinställningarna. Be serversystemadministratören kontrollera detta. Observera att tiden i DB är inställd på UTC som standard.

### Ändra sessionslagring

Försök att ändra sessionslagringen. Använd informationen från artikeln [Hitta dina sessionsfiler](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/storage/session-storage/sessions) i vår utvecklardokumentation för att ta reda på var din session är lagrad och ändra den genom att redigera filen `app/etc/env.php`.

Om du till exempel vill börja lagra sessionen i filsystemet ändrar du avsnittet `'session'` så här:

```php
....
'session' =>
    array (
      'save' => 'files',
),
....
```

Kör kommandot `bin/magento app:config:import` om du vill importera konfigurationsdata.


## Relaterad läsning

* [Importera data från konfigurationsfiler](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/cli/configuration-management/import-configuration) i utvecklardokumentationen
* [Konfigurera [!DNL Redis]](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/cache/redis/config-redis) i utvecklardokumentationen
* [Omdirigera tillbaka till inloggningsformuläret [!UICONTROL Commerce Admin] med felet&quot;Ditt konto är tillfälligt inaktiverat&quot; &#x200B;](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error) i vår kunskapsbas för support
* [Omdirigera tillbaka till inloggningsformuläret utan fel när du försöker logga in på [!UICONTROL Commerce Admin]](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin) i vår kunskapsbas för support
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook

