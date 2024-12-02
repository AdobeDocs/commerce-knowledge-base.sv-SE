---
title: 'PWA Studio: Valideringsfel när utvecklarläget körs'
description: I det här avsnittet beskrivs en lösning för när valideringsfel inträffar när utvecklarläget körs i PWA (Progressive Web App) Studio för Adobe Commerce på grund av att du inte tidigare har skapat miljöfilen venia-concept (Venia är en PWA storefront.). Den här filen innehåller variablerna för den lokala utvecklingsmiljön.
exl-id: 97d042ef-88e6-4eda-a834-2cff4de276e2
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# PWA Studio: Valideringsfel när utvecklarläget körs

I det här avsnittet beskrivs en lösning för när valideringsfel inträffar när utvecklarläget körs i PWA (Progressive Web App) Studio för Adobe Commerce på grund av att du inte tidigare har skapat miljöfilen venia-concept (Venia är en PWA storefront.). Den här filen innehåller variablerna för den lokala utvecklingsmiljön.

## Berörda produkter och versioner

* PWA Studio för Adobe Commerce

## Problem

<u>Steg för att återskapa</u>:

* Kör utvecklarläget i PWA Studio för Adobe Commerce.

<u>Förväntat resultat</u>:

* Servern PWA Studio startar normalt.

<u>Faktiskt resultat</u>:

* Valideringsfel kan se ut ungefär som:

```
    ⓧ  Missing required environment variables:         MAGENTO_BACKEND_URL: Connect to an instance of Adobe Commerce 2.3 by specifying its public domain name. (eg.         "https://master-7rqtwti-mfwmkrjfqvbjk.us-4.magentosite.cloud/")      ⚠  No .env file in ./packages/venia-concept. Autogenerate a .env file by running the command 'buildpack         create-env-file ./packages/venia-concept'.
```

## Orsak

Miljövariabelfilen för den lokala utvecklingsmiljön saknas. Filen som genereras av kommandot nedan innehåller variablerna för den lokala utvecklingsmiljön.

## Lösning

Kontrollera att du kör kommandot

```
npx @magento/pwa-buildpack create-env-file packages/venia-concept
```

i rotkatalogen för att generera filen som innehåller variablerna för den lokala utvecklingsmiljön.

## Relaterad läsning

* [PWA Studio för Adobe Commerce-dokumentation](https://magento.github.io/pwa-studio/)
* [Venia Storefront (Concept)](https://magento.github.io/pwa-studio/venia-pwa-concept/)
