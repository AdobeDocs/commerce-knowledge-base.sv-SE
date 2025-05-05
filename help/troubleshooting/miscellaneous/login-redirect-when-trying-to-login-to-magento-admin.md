---
title: Omdirigering vid inloggning till Commerce Admin
description: I den här artikeln beskrivs möjliga lösningar på inloggningsproblemet för Commerce Admin, där du omdirigeras tillbaka till inloggningsformuläret när du försöker logga in på Admin och inget felmeddelande visas. Detta inkluderar korrigering av serverns tidszonsinställningar och rensning av cookies-inställningarna i Adobe Commerce.
exl-id: ff3114fd-8690-4983-8221-cf807f083b15
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Omdirigering vid inloggning till Commerce Admin

I den här artikeln beskrivs möjliga lösningar på inloggningsproblemet för Commerce Admin, där du omdirigeras tillbaka till inloggningsformuläret när du försöker logga in på Admin och inget felmeddelande visas. Detta inkluderar korrigering av serverns tidszonsinställningar och rensning av cookies-inställningarna i Adobe Commerce.

## Berörda versioner:

Alla Adobe Commerce-versioner och -utgåvor.

## Problem

<u>Steg som ska återskapas</u>:

1. Gå till sidan Commerce Admin.
1. Ange dina inloggningsuppgifter och klicka på Logga in.

<u>Förväntade resultat</u>:

Du loggas in på Commerce Admin.

<u>Faktiska resultat</u>:

Du omdirigeras tillbaka till inloggningsformuläret utan några felmeddelanden.

## Orsak

Det finns några möjliga orsaker till problemet:

* Felaktig tidszon har angetts på webbläsarnivå (vilket leder till att admin-sessionen anses ha upphört att gälla även om dess faktiska livslängd ännu inte har löpt ut).
* Felaktiga inställningar för cookies, vilket leder till att den etablerade sessionen inte används av Adobe Commerce.

I nästa stycke hittar du lösningar i varje enskilt fall.

## Lösningar

### Livslängdsproblem för administratörssession

Försök använda en annan webbläsare och öka administratörssessionens livstid om den är mindre än en timme.

Så här ökar du administratörssessionens livstid:

1. Skapa en säkerhetskopia av databasen.
1. Använd ett databasverktyg som [phpMyAdmin](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) eller öppna databasen manuellt från kommandoraden för att köra följande SQL-fråga:

   ```sql
   UPDATE core_config_data SET value = 7200 WHERE path = 'admin/security/session_lifetime';
   ```

1. Rensa konfigurationscachen genom att köra följande kommando:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

### Felaktiga inställningar för cookies

Så här kontrollerar du cookies-inställningsvärdena och rensar dem:

1. Skapa en säkerhetskopia av databasen.
1. Använd ett databasverktyg som [phpMyAdmin](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) eller öppna databasen manuellt från kommandoraden för att köra följande SQL-fråga:

   ```sql
   SELECT * FROM core_config_data WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. Om värdenas svar inte är tomma anger du NULL genom att köra:

   ```sql
   UPDATE core_config_data SET value = NULL WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. Rensa konfigurationscachen genom att köra följande kommando:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

## Relaterade artiklar

* [Omdirigera tillbaka till administratörsinloggningsformuläret med felet&quot;Ditt konto är tillfälligt inaktiverat&quot; ](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md) i vår kunskapsbas för support.
* [Omdirigera tillbaka till inloggningsformuläret för administratörer med felet&quot;Din nuvarande session har gått ut&quot;](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-current-session-has-been-expired-error.md) i vår kunskapsbas för support.
