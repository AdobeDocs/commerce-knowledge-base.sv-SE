---
title: Lös problem med krypteringsnyckeln
description: I den här artikeln beskrivs hur du åtgärdar problem som orsakas av att krypteringsnyckeln inte flyttas tillsammans med DB-dumpen till den andra miljön.
exl-id: 34410da0-1bd5-421e-9cd7-d3ee75ad8ed7
feature: Cache, Variables
role: Developer
source-git-commit: 0458b37e2af4c9ad2ec92a1fdd6844ef222ef84a
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Lös problem med krypteringsnyckeln

I den här artikeln beskrivs hur du åtgärdar problem som orsakas av att krypteringsnyckeln inte flyttas tillsammans med DB-dumpen till den andra miljön.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur 2.4.x

## Problem

När du har importerat en [databassump](/help/how-to/general/create-database-dump-on-cloud.md) från produktionsmiljöer till mellanlagrings-/integreringsmiljöer visas sparade kreditkortsnummer som felaktiga och/eller betalningar misslyckas för betalningsintegreringar som kräver användning av handlarens autentiseringsuppgifter.

## Orsak

Krypteringsnyckeln som används för att kryptera känsliga data, som kreditkortsnummer och handlarens inloggningsuppgifter, lagras inte i databasen och överförs därför inte till en annan miljö efter import/export av databasdumpar.

## Lösning

Du måste kopiera krypteringsnyckeln från källmiljön och lägga till den i målmiljön.

Så här kopierar du krypteringsnyckeln:

1. SSH till ditt projekt som var källa för databasdumpen, vilket beskrivs i [SSH till miljön](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) i vår utvecklardokumentation.
1. Öppna `app/etc/env.php` i en textredigerare.
1. Kopiera värdet för `key` för `crypt`.

```php
return array ('crypt' =>      array ('key' => '<your encryption key>', ),);
```

Så här anger du nyckelvärdet för målprojektet:

1. Öppna [molnkonsolen](https://console.adobecommerce.com) och leta upp ditt projekt.
1. Ange värdet för variabeln [CRYPT\_KEY](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) (i vår utvecklardokumentation) enligt beskrivningen i [Konfigurera ditt projekt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html) i vår utvecklardokumentation. Detta utlöser distributionsprocessen och `CRYPT_KEY` åsidosätts i `app/etc/env.php`-filen för varje distribution.

Om du vill kan du manuellt åsidosätta krypteringsnyckeln i filen `app/etc/env.php`:

1. SSH till målmiljön.
1. Öppna `app/etc/env.php` i en textredigerare.
1. Klistra in kopierade data som `key`-värde för `crypt`.
1. Spara den redigerade `env.php`.
1. Rensa cacheminnet i målmiljön genom att köra `bin/magento cache:clean` eller Commerce Admin under **System** > **Verktyg** > **Cachehantering**.
