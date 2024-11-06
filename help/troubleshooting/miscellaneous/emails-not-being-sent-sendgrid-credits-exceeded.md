---
title: E-postmeddelanden skickas inte när SendGrid-krediter överskrids på Adobe Commerce
description: Den här artikeln innehåller en lösning när e-postmeddelanden inte skickas eftersom du har överskridit din kreditgräns för SendGrid på Adobe Commerce.
exl-id: 43438890-665b-4408-8034-e61de8fbbd8b
feature: Communications, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# E-postmeddelanden skickas inte när SendGrid-krediter överskrids på Adobe Commerce

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.3

## Problem

SendGrid-krediter avser antalet tillåtna e-postmeddelanden som kan skickas. Endast 12 000 e-postmeddelanden kan skickas per månad från integrerings- och mellanlagringsgrenarna. Krediterna förnyas i början av månaden, så om du får slut på krediter måste du vänta på förnyelsen.

Det finns inga strikta gränser för hur många e-postmeddelanden som kan skickas i produktionen, så länge Sender Reputation är över 95 %. Anseendet påverkas av antalet avvisade/avvisade e-postmeddelanden och om DNS-baserade skräppostregister har flaggat din domän som en potentiell skräppostkälla. I produktionen fördelas totalt 12 000 e-postmeddelanden per dag, men det antalet kan utökas baserat på det genomsnittliga antalet e-postmeddelanden som har skickats under de senaste fem dagarna.

## Så här kontrollerar du om dina krediter har överskridits:

Planarkitekturen för Adobe Commerce i molninfrastruktur Pro: Kontrollera `/var/log/mail.log` - du kan se ett meddelande som det här:

`May 28 21:13:00 <i-node> postfix/error[21335]: BC7941A2BBF: to=<to@email.com>, relay=none, delay=4642, delays=4642/0.56/0/0.03, dsn=4.0.0, status=deferred (delivery temporarily suspended: SASL authentication failed; server smtp.sendgrid.net[ip address] said: 451 Authentication failed: Maximum credits exceeded).`

## Orsak

Det finns begränsningar för hur många e-postmeddelanden som får skickas.

## Lösning

* Om det här meddelandet visas i produktionsmiljön [skickar du en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) och anger ovanstående meddelande och begär att krediterna ska höjas.
* Om du inte ser det här meddelandet eller om du är på Adobe Commerce om arkitekturen för Starter-planen för molninfrastruktur kan du även [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) och ange att filen `mail.log` inte anger att krediterna har överskridits.

## Relaterad läsning

* [SendGrid](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/sendgrid) i utvecklardokumentationen.
