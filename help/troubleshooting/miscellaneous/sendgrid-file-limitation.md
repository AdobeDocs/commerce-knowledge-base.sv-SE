---
title: '''[!DNL SendGrid] filbegränsning för Adobe Commerce Cloud'
description: I den här artikeln beskrivs  [!DNL SendGrid] begränsningar för Adobe Commerce vad gäller molninfrastruktur.
feature: Deploy, Marketing Tools
role: Developer, Admin
exl-id: 48629f48-8100-4128-9211-53d947aecd49
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# [!DNL SendGrid] begränsning för Adobe Commerce Cloud

Den här artikeln innehåller tillfälliga lösningar för [!DNL SendGrid] begränsningar för Adobe Commerce i molninfrastrukturen.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur, [alla versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)


## Problem

Du försöker skicka stora bilagor i e-postmeddelanden och ser följande loggfel:

I `/var/log/mail.log`

```shell
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[21408]: fatal: no-reply@xxxxxxxx.com(8080): message file too big
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[26434]: fatal: no-reply@xxxxxxxxx.com(8080): message file too big
```

I `/var/log/exception.log`

Produktion:

`/app/<project-id>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Mellanlagring:

`/app/<project-id_stg>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Mellanlagring2:

`/app/<project-id_stg2>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

## Orsak

[!DNL SendGrid] har en systembegränsning på 30 MB för e-post. Vi rekommenderar att du inte använder bilagor som överstiger 10 MB. Se [Skickar bifogade filer](https://docs.sendgrid.com/ui/sending-email/attachments-with-digioh) i dokumentationen för SendGrid om du vill ha mer information.

## Tillfällig lösning

* Använd inte bifogade filer som är större än 6 MB eller 10 MB.
* Överväg att använda en SMTP-fjärrserver på din Adobe Commerce-instans. Om du vill se steg går du till [Konfigurera e-postkommunikation](https://experienceleague.adobe.com/docs/commerce-admin/systems/communications/email-communications.html) i vår Admin Systems Guide.
* Konfigurera om servern så att filer kan sparas i modulen och bifoga sedan länken till filerna i e-postmeddelandena.

## Relaterad läsning

* [[!DNL SendGrid] e-posttjänst](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html) i vår Commerce on Cloud Infrastructure Guide.
