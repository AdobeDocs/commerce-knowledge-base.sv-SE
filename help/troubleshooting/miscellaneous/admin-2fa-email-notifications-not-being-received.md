---
title: Admin 2FA-e-postmeddelanden tas inte emot
description: I den här artikeln finns felsökning när du inte får e-postmeddelandet med anvisningar om hur du slutför installationen efter att du har konfigurerat Two-Factor Authentication (2FA) för att förbättra säkerheten för administratörsåtkomst i Adobe Commerce i molninfrastrukturen.
exl-id: 7ab6b2b4-6aca-4323-a45b-2b4e52955160
feature: Admin Workspace, Communications
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '300'
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
Eftersom du inte har åtkomst till administratören måste du infoga konfigurationen i databasen. Koppla in rätt e-postadress och kör MySQL-satsen:

   ```
   insert into core_config_data (scope,scope_id,path,value) values ('default',0,'trans_email/ident_general/email', your-email@here.com)
   ```

   * Om det returnerar ett resultat fortsätter du till **Steg 2**.

1. Om e-postmeddelandet visades i din skräppostmapp klickar du på länken i e-postmeddelandet. Om länken sedan har upphört att gälla kan du försöka logga in igen för att upprepa processen.
1. När du har fått åtkomst går du till **Store** > **Konfiguration** > **Allmänt** > **Lagra e-postadresser** och konfigurerar e-postadresserna.

### Steg 2: Om/när e-postadresserna har konfigurerats på rätt sätt kommer SSH in i miljön och kör det här kommandot:

```php
php -r "mail(<your email address>,<subject>,<content>,'To: <sender email>');"
```

Kontrollera din skräppostmapp för e-postmeddelandet. Om e-postmeddelandet visades där [skickar du en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#login) för att begära att domänen får en vit etikett i SendGrid.

## Relaterad läsning

* [SendGrid](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/sendgrid) i utvecklardokumentationen.
