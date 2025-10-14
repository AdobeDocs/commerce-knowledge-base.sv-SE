---
title: Kron-stopp på grund av felkonfigurerade eller saknade [!DNL OpCache] inställningar
description: Den här artikeln innehåller en lösning för när kroner slutar fungera på grund av felkonfigurerade eller saknade [!DNL OpCache] inställningar.
exl-id: 30643ea9-969f-41c8-8e62-b24e56d690cf
feature: Cache
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Kron stoppades på grund av felkonfigurerade eller saknade [!DNL OpCache]-inställningar

Den här artikeln innehåller en lösning för när kron slutar fungera på grund av att [!DNL OpCache]-inställningar saknas eller är felkonfigurerade.

## Berörda produkter och versioner

Adobe Commerce i molninfrastrukturen, [alla versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problem

Kronen slutade fungera.

## Orsak

Modulen [!DNL OpCache] uppdaterades till en nyare version som introducerade ett [!DNL GraphQL]-plugin som skriver om `env.php` i körningsmiljön och kan åsidosätta referensinställningen, som kan ha orsakat problemet. Konfigurationen [!DNL OpCache] måste uppdateras för att inga problem med `env.php file` ska uppstå. Den löstes i [&#x200B; version 2002.1.13](/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package.html?lang=en#v2002.1.13) av paketet [!DNL ECE Tools].

## Lösning

Alternativ 1: Kör följande i kommandoradsverktyget:

```bash
bin/magento cron:run
```

Ett meddelande kan visa att kronen är inaktiverad.

Alternativ 2: Öppna filen `app/etc/env.php` - om du ser nedan inaktiverades kranen manuellt, återaktiverades inte på grund av en misslyckad distribution eller så var problemet relaterat till inställningarna för [!DNL OpCache].

```php
  'cron' =>
  array (
    'enabled' => 0,
  ),
```

1. Om kronen är inaktiverad kör du det här kommandot för att aktivera kronen igen: `vendor/bin/ece-tools cron:enable`
1. Kontrollera att du har den senaste versionen av [!DNL ECE Tools]. Om du inte gör det, uppgradera (eller hoppa till punkt 3). Kör det här kommandot om du vill kontrollera din befintliga version:
   `composer show magento/ece-tools`
1. Om du redan har den senaste versionen av [!DNL ECE Tools] kontrollerar du om filen `op-exclude.txt` finns. Gör så här:
   `ls op-exclude.txt`.
Om den här filen inte finns lägger du till https://github.com/magento/magento-cloud/blob/master/op-exclude.txt i svaret och implementerar sedan ändringen och distribuerar om.
1. Om du inte behöver uppgradera [!DNL ECE Tools] kan du även lägga till/ändra https://github.com/magento/magento-cloud/blob/master/op-exclude.txt i ditt svar och sedan genomföra ändringen och omdistribuera den.

## Relaterad läsning

* [Problem med beredskapskontroll av kron](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues.html)
* [Egenskapen Crons](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html)
* [Kronjobbet har fastnat i körningsstatus](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
