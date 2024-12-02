---
title: 'PWA Studio: webbläsaren litar inte på det SSL-certifikat som genererats'
description: I den här artikeln finns en lösning på en otillförlitlig, genererad SSL-certifikatvarning i webbläsaren när du navigerar till en lokal instans av PWA Studio storefront under utvecklingen.
exl-id: b7bfe1e6-5832-4472-9e51-f04b8583428a
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# PWA Studio: webbläsaren litar inte på det SSL-certifikat som genererats

I den här artikeln finns en lösning på en otillförlitlig, genererad SSL-certifikatvarning i webbläsaren när du navigerar till en lokal instans av PWA Studio storefront under utvecklingen.

## Berörda produkter och versioner

PWA Studio för Adobe Commerce

## Problem

Webbläsaren litar inte på det genererade SSL-certifikatet för din lokala PWA Studio storeFront.

## Orsak

Bläddra till webbplatsen dev/staging.

## Lösning

I ditt storefront-projekt kör du kommandot för att lägga till ett anpassat värdnamn och SSL-certifikat till den lokala utvecklingsinstansen:

```sh
yarn buildpack create-custom-origin ./
```

Generering av certifikat hanteras av [devcert](https://github.com/davewasmer/devcert). Det beror på OpenSSL, så kontrollera att du har en aktuell version av openssl på datorn med följande kommando:

`openssl version`

Versionen ska vara 1.0 eller högre (eller LibreSSL 2, för OSX High Sierra).

Du kan installera senare versioner av OpenSSL med [Homebrew](https://brew.sh/) i OSX, [Chocolatey](https://chocolatey.org/) i Windows eller med Linux-distributionens pakethanterare.

Om du kör Linux kontrollerar du att `libnss3-tools` (eller motsvarande) är installerat på datorn. Ytterligare information finns i det här avsnittet av Viktigt för [devcert](https://github.com/davewasmer/devcert#skipcertutil).

En del användare har föreslagit att devcert-mappen ska tas bort för att utlösa certifikatomgenerering.

* För MacOS-användare finns den här mappen vanligtvis på: `{{~/Library/Application Support/devcert }}`
* För Windows-användare finns den här mappen vanligtvis på: `${User}\AppData\Local\devcert`

## Relaterad läsning i vår kunskapsbas

* [PWA Studio: Självsignerat certifikatförtroendefel](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio: Webpack låser sig innan kompileringen påbörjas](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio: Webbläsaren visar felet&quot;Det går inte att skriva proxy till&quot;](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio: Valideringsfel när utvecklarläget körs](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
