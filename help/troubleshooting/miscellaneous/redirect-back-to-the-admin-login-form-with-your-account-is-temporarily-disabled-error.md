---
title: Omdirigera tillbaka till inloggningsformuläret för Commerce Admin med felmeddelandet"Ditt konto är tillfälligt inaktiverat"
description: 'I den här artikeln beskrivs möjliga lösningar på inloggningsproblemet för Commerce Admin, där du omdirigeras tillbaka till inloggningsformuläret med följande felmeddelande: *"Ditt konto är tillfälligt inaktiverat"*. Den föreslagna lösningen är att kontrollera och korrigera inställningarna för administratörsanvändardatabasen.'''
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Omdirigera tillbaka till inloggningsformuläret för Commerce Admin med felmeddelandet&quot;Ditt konto är tillfälligt inaktiverat&quot;

Den här artikeln innehåller möjliga lösningar på inloggningsproblemet för Commerce Admin, där du omdirigeras tillbaka till inloggningsformuläret med följande felmeddelande: *&quot;Ditt konto är tillfälligt inaktiverat&quot;*. Den föreslagna lösningen är att kontrollera och korrigera inställningarna för administratörsanvändardatabasen.

## Berörda versioner:

Alla Adobe Commerce-versioner och -utgåvor

## Problem

<u>Steg som ska återskapas</u>:

1. Gå till sidan Commerce Admin.
1. Ange dina inloggningsuppgifter och klicka på Logga in.

<u>Förväntat resultat</u>:

Du loggas in på Commerce Admin.

<u>Faktiskt resultat</u>:

Du omdirigeras tillbaka till inloggningsformuläret med följande felmeddelande: *Ditt konto är tillfälligt inaktiverat. Försök igen senare.*.

## Lösning

1. Skapa en säkerhetskopia av databasen.
1. Använd ett databasverktyg som [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin) eller öppna databasen manuellt från kommandoraden. I databastabellen `admin_user` kontrollerar du om `is_active` är inställd på `1` och `lock_expires` är `NULL` för din administratörsanvändarpost. Återställ dessa värden om det behövs.

## Relaterad läsning i vår kunskapsbas

* [Omdirigera tillbaka till inloggningsformuläret utan fel när du försöker logga in på Commerce Admin](/help/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin.md)
