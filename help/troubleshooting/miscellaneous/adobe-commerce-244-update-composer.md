---
title: Problem med plugin-program för Composer vid uppgradering till Adobe Commerce 2.4.4
description: Den här artikeln innehåller en lösning som undviker problemet med plugin-program för disposition när du uppgraderar från Adobe Commerce 2.4.3 och tidigare till Adobe Commerce 2.4.4 eller senare (när framtida versioner släpps).
exl-id: 7502ca9e-c307-4e8a-aa1d-4886e7be25da
feature: Upgrade
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# Problem med plugin-program för Composer vid uppgradering till Adobe Commerce 2.4.4

Den här artikeln innehåller en lösning för att undvika problem med plugin-program för disposition när du uppgraderar från Adobe Commerce 2.4.3 och tidigare till Adobe Commerce 2.4.4 eller senare (när framtida versioner släpps).

## Berörda produkter och versioner

* Adobe Commerce lokalt, alla versioner när de uppdateras till 2.4.4 eller senare (när de släpps)
* Adobe Commerce i molninfrastruktur, alla versioner när de uppdateras till 2.4.4 eller senare (när de släpps)
* Magento Open Source, alla versioner vid uppdatering till 2.4.4 eller senare (när de släpps)

## Problem

När du uppdaterar till Adobe Commerce 2.4.4 eller senare efter juli 2022 kan du få en varning från dispositionen om plugin-program.

<u>Steg som ska återskapas</u>:

Krav: Adobe Commerce 2.4.3 eller tidigare är installerat.

1. Starta uppgraderingen enligt beskrivningen i [Utför en uppgradering](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html).
1. Kör kommandot `composer update` för att uppgradera Adobe Commerce-programmet.

<u>Förväntade resultat</u>:

Uppgraderingen är klar.

<u>Faktiska resultat</u>:

Installationen misslyckas med ett fel som liknar följande:

```bash
Writing lock file
Installing dependencies from lock file (including require-dev)
Package operations: 591 installs, 0 updates, 0 removals
  - Installing laminas/laminas-dependency-plugin (2.2.0): Extracting archive
laminas/laminas-dependency-plugin contains a Composer plugin which is currently not in your allow-plugins config. See https://getcomposer.org/allow-plugins
Do you trust "laminas/laminas-dependency-plugin" to execute code and wish to enable it now? (writes "allow-plugins" to composer.json) [y,n,d,?] y
Plugin initialization failed (require(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory), uninstalling plugin
  - Removing laminas/laminas-dependency-plugin (2.2.0)
    Install of laminas/laminas-dependency-plugin failed


  [ErrorException]
  require(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## Orsak

Efter juli 2022 ändrar Composer standardvärdet för alternativet [`allow-plugins` ](https://getcomposer.org/doc/06-config.md#allow-plugins) till `{}` och plugin-program läses inte in längre om det inte tillåts.

## Lösning

Lägg till följande i din `composer.json`-fil, beroende på hur du har installerat Adobe Commerce:

* Om projektet har skapats [med `composer create-project`-kommandot](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html#get-the-metapackage):

  ```json
  "config": {
      "allow-plugins": {
          "dealerdirect/phpcodesniffer-composer-installer": true,
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

* Om projektet har skapats på ett annat sätt och inte har `"dealerdirect/phpcodesniffer-installer"` i avsnittet `"require-dev"`:

  ```json
  "config": {
      "allow-plugins": {
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

När du har uppdaterat filen `composer.json` kör du kommandot `composer update` och startar om uppgraderingsprocessen.
