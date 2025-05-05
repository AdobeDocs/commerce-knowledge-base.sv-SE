---
title: Dirigera om till överordnad miljö vid åtkomst till den nya integreringsmiljön
description: I den här artikeln finns felsökningsanvisningar för Adobe Commerce om molninfrastrukturproblem där du i stället försöker komma åt den nyligen skapade integreringsmiljön.
exl-id: d1d40c8d-d43c-442e-95c9-76f3cdcafb0e
feature: Cache, Integration, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Dirigera om till överordnad miljö vid åtkomst till den nya integreringsmiljön

I den här artikeln finns felsökningsanvisningar för Adobe Commerce om molninfrastrukturproblem där du i stället försöker komma åt den nyligen skapade integreringsmiljön.

För att åtgärda detta måste du korrigera bas-\_url-värdet i databasen och se till att variabelvärdet `UPDATE_URLS` är inställt på `true`. Mer information finns i avsnitten nedan.

Berörda versioner och utgåvor:

* Adobe Commerce i molninfrastruktur 2.X.X

## Problem

<u>Steg som ska återskapas</u>:

1. Klona den befintliga integreringsgrenen.
1. Klicka på URL:en för att komma åt den nya miljön.

<u>Förväntat resultat</u>:

Du kommer till den nya miljön.

<u>Faktiskt resultat</u>:

Du omdirigeras till miljön i den överordnade grenen.

## Lösning

För att åtgärda problemet måste du korrigera `base_url`-värdena (säkra och osäkra) i den anpassade miljödatabasen och ange variabeln `UPDATE_URL` i filen `.magento.env.yaml`.

### Korrigera bas-\_url-värden i databasen

Ändringar i databasen kan göras antingen manuellt eller med Adobe Commerce CLI, om du har version 2.2.0 eller senare.

#### Korrigera värdena i databasen manuellt

1. Anslut till databasen.
1. Kör följande kommandon:

```sql
UPDATE core_config_data SET value = %your_new_environment_unsecure_url% WHERE path="web/unsecure/base_url"
```

```sql
update core_config_data set value = %your_new_environment_secure_url% where path="web/secure/base_url"
```

#### Korrigera databasen med Adobe Commerce CLI (finns för version 2.2.X)

1. Logga in som, eller växla till, ägare av [Adobe Commerce-filsystemet](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/web-server/apache.html?lang=sv-SE).
1. Kör följande kommandon:

```bash
php <your_magento_install_dir>/bin/magento config:set web/unsecure/base_url http://example.com
php <your_magento_install_dir>/bin/magento config:set web/secure/base_url https://example.com
```

### Ange variabeln `UPDATE_URLS`

I den lokala kodbasen i filuppsättningen `.magento.env.yaml`:

```
 stage:
    deploy:
        UPDATE_URLS: true
```

### Rensa konfigurationscache

Rensa konfigurationscachen genom att köra följande kommando för att ändringarna ska tillämpas:

```bash
php <your_magento_install_dir>/bin/magento cache:clean config
```

## Relaterad artikel i vår utvecklardokumentation:

[Distribuera variabler](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=sv-SE)
