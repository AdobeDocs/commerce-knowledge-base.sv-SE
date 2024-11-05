---
title: Reducera utgångna "oauth_tokens" före uppgradering 2.4.6
description: I den här artikeln finns en lösning på problemet där du ser ett stort antal "auth_tokens" i tabellen "oauth_token", vilket kan orsaka en lång fördröjning vid uppgradering till version 2.4.6. Vi rekommenderar att du reducerar tabellen Oauth_token med CleanExpiredTokens.php.
feature: Variables, Upgrade
role: Developer
exl-id: 92d1d15a-04da-4ba4-b6b8-5c491af9c4c1
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Minska utgången `oauth_tokens` före uppgradering 2.4.6

Den här artikeln ger en lösning på problemet där ett stort antal `oauth_tokens` visas i din `oauth_token`-tabell, vilket kan göra att det tar lång tid att uppgradera till version 2.4.6. Vi rekommenderar att du reducerar tabellen `oauth_token` genom att använda jobbet [`CleanExpiredTokens.php` ](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] för att ta bort utgångna token.

## Berörda produkter och versioner

* Adobe Commerce 2.4.0 - 2.4.6, alla distributionsmetoder

## Problem

Om det finns ett stort antal `oauth_tokens` i din `oauth_token`-tabell kan det orsaka en lång fördröjning när du uppgraderar till version 2.4.6.

Uppgraderingsprocessen inkluderar kryptering av dessa tokens för ett extra säkerhetslager, och den görs bara 100 poster åt gången. Detta kan ta flera timmar om det finns ett stort antal tokens.

Om du minskar ett stort antal `oauth_tokens` i `oauth_token`-tabellen kan det medföra att det tar lång tid att uppgradera till version 2.4.6.

## Lösning

Innan du startar en uppgradering måste du kontrollera att jobbet [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] körs. Det minskar storleken på tabellen `oauth_token` genom att ta bort de `oauth_tokens`-tokens som har upphört att gälla och bör redan vara aktiverat som standard.

Kör om du vill aktivera [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron]-jobbet manuellt:
```bin/magento cron:run --group=default```

## Relaterad läsning

* [Tjänster > [!DNL OAuth]](https://experienceleague.adobe.com/docs/commerce-admin/config/services/oauth.html) i referenshandboken för Commerce-konfigurationen
* [Autentiseringshandbok](https://developer.adobe.com/developer-console/docs/guides/authentication/) i Adobe Developer-handboken
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
