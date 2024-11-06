---
title: Omdirigering tillbaka till inloggningsformuläret [!UICONTROL Commerce Admin] med felet"Ditt konto är tillfälligt inaktiverat"
description: 'I den här artikeln beskrivs möjliga lösningar på inloggningsproblemet för Commerce Admin, där du omdirigeras tillbaka till inloggningsformuläret med följande felmeddelande: *"Ditt konto är tillfälligt inaktiverat"*. Den föreslagna lösningen är att kontrollera och korrigera inställningarna för administratörsanvändardatabasen.'''
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Omdirigera tillbaka till inloggningsformuläret [!UICONTROL Commerce Admin] med felet&quot;Ditt konto är tillfälligt inaktiverat&quot;

Den här artikeln innehåller möjliga lösningar på inloggningsproblemet [!UICONTROL Commerce Admin], där du omdirigeras tillbaka till inloggningsformuläret med följande felmeddelande: *&quot;Ditt konto är tillfälligt inaktiverat&quot;*. Den föreslagna lösningen är att kontrollera och korrigera inställningarna för administratörsanvändardatabasen.

## Berörda versioner:

Alla Adobe Commerce-versioner och -utgåvor

## Problem

<u>Steg som ska återskapas</u>:

1. Gå till sidan **[!UICONTROL Commerce Admin]**.
1. Ange dina autentiseringsuppgifter och klicka på **Logga in**.

<u>Förväntat resultat</u>:

Du loggas in på [!UICONTROL Commerce Admin].

<u>Faktiskt resultat</u>:

Du omdirigeras tillbaka till inloggningsformuläret med följande felmeddelande: *Ditt konto är tillfälligt inaktiverat. Försök igen senare.*.

## Lösning

1. Skapa en säkerhetskopia av databasen.
1. Använd ett databasverktyg som [[!DNL phpMyAdmin]](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) eller öppna databasen manuellt från kommandoraden. I databastabellen `admin_user` kontrollerar du om `is_active` är inställd på `1` och `lock_expires` är `NULL` för din administratörsanvändarpost. Återställ dessa värden om det behövs.

## Relaterad läsning

* [Omdirigera tillbaka till inloggningsformuläret utan fel vid inloggning till [!UICONTROL Commerce Admin]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin)
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
