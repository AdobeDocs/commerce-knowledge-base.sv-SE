---
title: '''[!DNL B2B] 1.4.0-installationen misslyckas på Adobe Commerce 2.4.6-p1 lokal'
description: I den här artikeln finns en lösning på problemet med lokal användning av Adobe Commerce 2.4.6-p1 där [!DNL B2B] installation av version 1.4.0 misslyckas.
feature: Install, Upgrade, B2B
role: Developer
exl-id: 4a557c13-7ec2-4cfe-b86e-bb0d1a441658
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# [!DNL B2B] 1.4.0-installationen misslyckas på Adobe Commerce 2.4.6-p1 lokalt

I den här artikeln finns en lösning på problemet med lokal användning av Adobe Commerce 2.4.6-p1 där [!DNL B2B] installation av version 1.4.0 misslyckas.

## Berörda produkter och versioner

* Adobe Commerce 2.4.6-p1 **lokal**
* [!DNL B2B] version 1.4.0

>[!NOTE]
>
>[!DNL B2B] version 1.4.0 har installerats **Adobe Commerce Cloud 2.4.6-p1**.

## Problem

<u>Steg som ska återskapas</u>:

1. Installera Adobe Commerce 2.4.6-p1.

   ```terminal
   m2install.sh -s composer --ee -v 2.4.6-p1
   ```

1. Försök installera [!DNL B2B] version 1.4.0.

   ```terminal
   composer require magento/extension-b2b:1.4.0
   ```

<u>Förväntade resultat</u>:

[!DNL B2B] version 1.4.0 installeras på Adobe Commerce 2.4.6-p1.

<u>Faktiska resultat</u>:

Installationen misslyckas med följande fel:

```terminal
Your requirements could not be resolved to an installable set of packages.

  Problem 1
    - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
    - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.


Installation failed, reverting ./composer.json and ./composer.lock to their original content.
```

## Tillfällig lösning

Installationen eller uppgraderingen av [!DNL B2B] version 1.4.0 på Adobe Commerce 2.4.6-p1 genom att lägga till manuella beroenden för [!DNL B2B] säkerhetspaket med [stabilitetstagg](https://getcomposer.org/doc/04-schema.md#package-links).

1. Uppdatera från Adobe Commerce installationskatalog `composer.json` med nödvändiga beroenden:

   ```terminal
   composer require magento/module-re-captcha-company=1.0.3-beta1@beta magento/security-package-b2b=1.0.4-beta1@beta
   ```

   **Kommandoutdata:**

   ```terminal
   Running composer update magento/module-re-captcha-company magento/security-package-b2b
   Loading composer repositories with package information
   Updating dependencies
   Lock file operations: 2 installs, 0 updates, 0 removals
     - Locking magento/module-re-captcha-company (1.0.3-beta1)
     - Locking magento/security-package-b2b (1.0.4-beta1)
   Writing lock file
   Installing dependencies from lock file (including require-dev)
   Package operations: 2 installs, 0 updates, 0 removals
     - Downloading magento/module-re-captcha-company (1.0.3-beta1)
     - Installing magento/module-re-captcha-company (1.0.3-beta1): Extracting archive
     - Installing magento/security-package-b2b (1.0.4-beta1)
   1 package suggestions were added by new dependencies, use `composer suggest` to see details.
   Package sebastian/phpcpd is abandoned, you should avoid using it. No replacement was suggested.
   Generating autoload files
   132 packages you are using are looking for funding.
   Use the `composer fund` command to find out more!
   No security vulnerability advisories found
   ```

1. Uppdatera `composer.json` att lägga till [!DNL B2B] version 1.4.0.

   ```terminal
   composer require magento/extension-b2b=1.4.0
   ```

   **Kommandoutdata:**

   ```terminal
   ./composer.json has been updated
   Running composer update magento/extension-b2b
   Loading composer repositories with package information
   Updating dependencies
   ...
   Generating autoload files
   132 packages you are using are looking for funding.
   Use the `composer fund` command to find out more!
   No security vulnerability advisories found
   ```

1. Slutför installations- eller uppgraderingsprocessen.

   * [Installera [!DNL B2B] om molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/b2b-module.html)
   * [Installera lokalt](https://experienceleague.adobe.com/docs/commerce-admin/b2b/install.html)
