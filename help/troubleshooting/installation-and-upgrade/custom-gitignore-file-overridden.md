---
title: Installationskommandot för Composer åsidosätter .gitignore-filen, Adobe Commerce
description: Den här artikeln innehåller en lösning för när en spårad `.gitignore`-fil åsidosätts av en kompositör på Adobe Commerce i molninfrastrukturen 2.4.2-p1 och 2.3.7.
exl-id: b0604bae-d630-4292-88d7-6945db30fcf4
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Installationskommandot för Composer åsidosätter .gitignore-filen, Adobe Commerce

Den här artikeln innehåller en lösning för när en spårad `.gitignore` filen åsidosätts av dispositionen på Adobe Commerce i molninfrastrukturen 2.4.2-p1 och 2.3.7.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur 2.4.2-p1 och 2.3.7.

## Problem

`.gitignore` filen skrivs över när du kör installationskommandot för disposition.

<u>Steg som ska återskapas</u>:


1. Skapa en tom katalog för arbetsytan.
1. Kör det här kommandot i rotkatalogen:

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition:2.4.2-p1.
   ```

   \# eller 2.3.7

1. Kör sedan följande kommandon:
   1. `echo "/this/line/should/stay" >> .gitignore`
   1. `git init`
   1. `git add * && git add .*`
   1. `git commit -m "Init"` # fil har implementerats för att repo
   1. `rm -rf vendor/*`
   1. `composer install`
   1. `git diff`

      ```git
      diff --git a/.gitignore b/.gitignore
      index c144521..7092a56 100644
      --- a/.gitignore
      +++ b/.gitignore
      @@ -70,4 +70,3 @@ atlassian*
      /generated/*
      !/generated/.htaccess
      .DS_Store
      -/this/line/should/stay
      ```

<u>Förväntat resultat</u>:

`.gitignore` åsidosätts inte av disposition.

<u>Faktiskt resultat</u>:

`.gitignore` åsidosätts av varje installationskörning av en disposition.

## Lösning

Behåll dina egna `.gitignore file` du måste ignorera det i `magento-deploy-ignore` -avsnitt.

```git
{
...
"extra": {
    "magento-deploy-ignore": {
        "*": [
            "/.gitignore"
        ]
    }
    ...
}
```


## Relaterad läsning

* [Den spårade .gitignore-filen åsidosätts av kompositören.](https://github.com/magento/magento2/issues/32888) i Magento2 GitHub.
