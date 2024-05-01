---
title: Admin 2FA-e-postmeddelanden tas inte emot
description: I den här artikeln finns felsökning när du inte får e-postmeddelandet med anvisningar om hur du slutför installationen efter att du har konfigurerat Two-Factor Authentication (2FA) för att förbättra säkerheten för administratörsåtkomst i Adobe Commerce i molninfrastrukturen.
exl-id: 7ab6b2b4-6aca-4323-a45b-2b4e52955160
feature: Admin Workspace, Communications
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Admin 2FA-e-postmeddelanden tas inte emot


## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur, alla versioner

## Problem

Du har konfigurerat Tvåfaktorautentisering för att förbättra säkerheten för administratörsåtkomst, men du får inte e-postmeddelandet med instruktionerna om hur du slutför konfigurationen.

## Orsak

Om du inte har konfigurerat avsändarens e-post korrekt, eller om din domän inte har fått en vit etikett i SendGrid, kommer e-postmeddelandet troligtvis att ha hamnat i skräppostmappen.

## Felsökning

### Steg 1: Kontrollera skräppostmappen

1. Om e-postmeddelandet inte visas i skräppostmappen kör du den här Mysql-frågan för att verifiera att e-postadresserna har konfigurerats:

   ```sql
   select * from core_config_data where path like '%trans_email%';
   ```

   * Om det inte returnerar några resultat betyder det att avsändaradressen inte har konfigurerats.
   * Om det returnerar ett resultat fortsätter du till **Steg 2**.

1. Om e-postmeddelandet visades i din skräppostmapp klickar du på länken i e-postmeddelandet. Om länken sedan har upphört att gälla kan du försöka logga in igen för att upprepa processen.
1. När du har fått tillgång till tjänsten går du till **Lager** > **Konfiguration** > **Allmänt** > **E-postadresser för butik** och konfigurera e-postadresserna.

### Steg 2: Om/när e-postadresserna har konfigurerats på rätt sätt kommer SSH in i miljön och kör det här kommandot:

```php
php -r "mail(<your email address>,<subject>,<content>,'To: <sender email>');"
```

Kontrollera din skräppostmapp för e-postmeddelandet. Om e-postmeddelandet visades där, [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#login) för att begära att domänen ska vara vit-märkt i SendGrid.

## Relaterad läsning

* [SendGrid](https://devdocs.magento.com/cloud/project/sendgrid.html) i vår dokumentation för utvecklare.
