---
title: Problem med komponentberoendekontroll
description: Den här artikeln innehåller lösningar på konflikter för komponentberoenden.
exl-id: e0865226-2aaf-4bdd-8c28-28f32f38ce0c
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Problem med komponentberoendekontroll

Den här artikeln innehåller lösningar på konflikter för komponentberoenden.

## Lös konflikter för komponentberoenden {#resolve-component-dependency-conflicts}

Vi föreslår att du provar följande lösningar i den ordning som visas:

1. [Beroenden i konflikt](#trouble-depend-conflict)
1. [Behörighetsproblem i filsystemet](#trouble-depend-permission)
1. [Status för komponentberoendekontroll ändras aldrig](#trouble-depend-state)

### Beroenden i konflikt {#trouble-depend-conflict}

Meddelandet *Komponentberoenden som står i konflikt* visas om Composer inte kan avgöra vilka komponenter som ska installeras eller uppdateras. För att lösa komponentberoendeproblem bör du vara en teknisk person som är väl insatt i hur Composer fungerar.

Följande är ett exempel på felmeddelande:

```terminal
We found conflicting component dependencies.
 You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
 We've detected conflicts with the following packages:
 - magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

>[!NOTE]
>
>Det meddelande du ser kommer troligtvis att vara annorlunda.

Se [Komponentberoenden i konflikt för en lösning](/help/troubleshooting/miscellaneous/conflicting-component-dependencies.md) i vår kunskapsbas för support.

## Behörighetsproblem i filsystemet {#trouble-depend-permission}

Om filsystemsägaren i Adobe Commerce inte har behörighet att skriva till kataloger i Adobe Commerce-filsystemet visas ett meddelande som liknar det här:

```terminal
file_put_contents(/var/www/html/magento2/var/composer_home/cache/repo/https---
packagist.org/provider-doctrine$instantiator.json): failed to open stream: Permission denied
```

Se till att du anger filsystembehörigheter enligt beskrivningen i artikeln [Översikt över ägarskap och behörigheter](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html) i utvecklardokumentationen.

## Status för komponentberoendekontroll ändras aldrig {#trouble-depend-state}

I vissa fall ändras inte statusen för komponentberoendekontrollen, även om du försöker åtgärda problemen. I så fall kan du antingen ta bort eller byta namn på filer med namnen `<magento_root>/var/.update_cronjob_status` och `<magento_root>/var/.setup_cronjob_status` och försöka köra komponenthanteraren igen.

Om du byter namn på eller tar bort dessa filer måste komponenthanteraren köra kontrollerna igen.
