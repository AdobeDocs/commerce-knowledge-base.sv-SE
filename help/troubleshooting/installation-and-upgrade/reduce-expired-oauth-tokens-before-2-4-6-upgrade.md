---
title: Reducera utgångna "oauth_tokens" före uppgradering 2.4.6
description: I den här artikeln finns en lösning på problemet där du ser ett stort antal "auth_tokens" i tabellen "oauth_token", vilket kan orsaka en lång fördröjning vid uppgradering till version 2.4.6. Vi rekommenderar att du reducerar tabellen Oauth_token med CleanExpiredTokens.php.
feature: Variables, Upgrade
role: Developer
exl-id: 92d1d15a-04da-4ba4-b6b8-5c491af9c4c1
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Minska utgången `oauth_tokens` före uppgradering till 2.4.6

Den här artikeln innehåller en lösning på ett problem där du ser ett stort antal `oauth_tokens` i `oauth_token` tabell, vilket kan medföra en lång fördröjning vid uppgradering till version 2.4.6. Vi rekommenderar att du minskar `oauth_token` tabellen med [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] jobb för att ta bort utgångna token.

## Berörda produkter och versioner

* Adobe Commerce 2.4.0 - 2.4.6, alla distributionsmetoder

## Problem

Om det finns många `oauth_tokens` i `oauth_token` som kan orsaka en lång fördröjning vid uppgradering till version 2.4.6.

Uppgraderingsprocessen inkluderar kryptering av dessa tokens för ett extra säkerhetslager, och den görs bara 100 poster åt gången. Detta kan ta flera timmar om det finns ett stort antal tokens.

Minska ett stort antal `oauth_tokens` i `oauth_token` tabellen kan förhindra en lång fördröjning vid uppgradering till version 2.4.6.

## Lösning

Innan du påbörjar en uppgradering måste du se till att [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] jobbet körs. Det minskar storleken på `oauth_token` tabell genom att ta bort utgångna `oauth_tokens` och ska redan vara aktiverat som standard.

Så här utlöser du [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] jobb, kör:
```bin/magento cron:run --group=default```

## Relaterad läsning

* [Tjänster > [!DNL OAuth]](https://experienceleague.adobe.com/docs/commerce-admin/config/services/oauth.html) i referenshandboken för Commerce Configuration.
* [Autentiseringshandbok](https://developer.adobe.com/developer-console/docs/guides/authentication/) i Adobe Developer Guide.
