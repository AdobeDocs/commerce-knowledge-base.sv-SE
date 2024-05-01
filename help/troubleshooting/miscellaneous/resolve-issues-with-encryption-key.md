---
title: Lös problem med krypteringsnyckeln
description: I den här artikeln beskrivs hur du åtgärdar problem som orsakas av att krypteringsnyckeln inte flyttas tillsammans med DB-dumpen till den andra miljön.
exl-id: 34410da0-1bd5-421e-9cd7-d3ee75ad8ed7
feature: Cache, Variables
role: Developer
source-git-commit: bee0263da487399ab07bf9158c4d60ab316d6ea1
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Lös problem med krypteringsnyckeln

I den här artikeln beskrivs hur du åtgärdar problem som orsakas av att krypteringsnyckeln inte flyttas tillsammans med DB-dumpen till den andra miljön.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.2.x, 2.3.x

## Problem

Efter import av en [databasdump](/help/how-to/general/create-database-dump-on-cloud.md) från produktionsmiljö till mellanlagrings-/integreringsmiljö, där sparade kreditkortsnummer verkar vara fel och/eller betalningar misslyckas för betalningsintegreringar som kräver användning av handlarens autentiseringsuppgifter.

## Orsak

Krypteringsnyckeln som används för att kryptera känsliga data, som kreditkortsnummer och handlarens inloggningsuppgifter, lagras inte i databasen och överförs därför inte till en annan miljö efter import/export av databasdumpar.

## Lösning

Du måste kopiera krypteringsnyckeln från källmiljön och lägga till den i målmiljön.

Så här kopierar du krypteringsnyckeln:

1. SSH till ditt projekt som var källa för databasdumpen, enligt beskrivningen i [SSH till miljö](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) i vår dokumentation för utvecklare.
1. Öppna `app/etc/env.php` i en textredigerare.
1. Kopiera värdet för `key` for `crypt`.

```php
return array ('crypt' =>      array ('key' => '<your encryption key>', ),);
```

Så här anger du nyckelvärdet för målprojektet:

1. Öppna [Cloud Console](https://console.adobecommerce.com) och hitta ditt projekt.
1. Ange värdet för [CRYPT\_KEY](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) (i vår utvecklardokumentation), enligt beskrivningen i [Konfigurera ditt projekt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html) i vår dokumentation för utvecklare. Detta kommer att starta distributionsprocessen och `CRYPT_KEY` åsidosätts i `app/etc/env.php` på alla distributioner.

Om du vill kan du manuellt åsidosätta krypteringsnyckeln i `app/etc/env.php` fil:

1. SSH till målmiljön.
1. Öppna `app/etc/env.php` i en textredigerare.
1. Klistra in kopierade data som `key` värde för `crypt`.
1. Spara de redigerade `env.php`.
1. Rensa cacheminnet i målmiljön genom att köra `bin/magento cache:clean` eller i Commerce Admin under **System** > **verktyg** > **Cachehantering**.
