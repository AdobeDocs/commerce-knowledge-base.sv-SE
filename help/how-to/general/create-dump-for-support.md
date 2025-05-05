---
title: Så här skapar du en"scrubbed"-dump på supportagentens begäran
description: I den här artikeln finns information om hur du skapar en"rensad" dump (säkerhetskopia) av din databas och kod från Adobe Commerce Admin när du ombeds att tillhandahålla en sådan av en Adobe Commerce supportagent. Den här dumpen exkluderar dina mediefiler för att snabba upp processen och resultera i en mycket mindre fil. Alla känsliga data hashas när databassäkerhetskopieringen görs.
exl-id: ad088bd2-3f92-416e-89f0-d037d53cd6a9
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# Så här skapar du en&quot;scrubbed&quot;-dump på supportagentens begäran


## Berörda produkter och versioner

Adobe Commerce (alla distributionsmetoder) 2.3.x, 2.4.x.

## Skapa en&quot;scrubbed&quot;-dump

Skapa en&quot;scrubbed&quot;-dump från administratören:

1. Gå till **System** > **Support** > **Datainsamling** i Commerce Admin.
1. Klicka på **Ny säkerhetskopia**.
1. Efter några minuter klickar du på **Uppdatera status** (kan ta längre tid, upprepa var femte minut tills det är klart).
1. Flytta de genererade dumpfilerna från katalogen `/var/support` till Adobe Commerce rotkatalog.

Du kan sedan ange till Support att länken för direkthämtning till dumpfilerna (din butiksadress och filnamnet som visas) finns.

Om du har problem med att skapa dumpar från Admin kan du använda CLI-kommandon enligt beskrivningen i [Kör supportverktygen](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/cli/run-support-utilities) i utvecklardokumentationen.

## Relaterad läsning

* [Skapa fullständig databassäkerhetskopiering för Adobe Commerce i molninfrastruktur](/help/how-to/general/create-database-dump-on-cloud.md) i vår kunskapsbas för support.
