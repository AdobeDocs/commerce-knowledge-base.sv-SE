---
title: 'PWA Studio: Webpack låser sig innan kompileringen påbörjas'
description: I den här artikeln beskrivs en föreslagen lösning för när ett javascript-skript [Webpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack) låser sig länge innan kompileringen börjar i Progressive Web App Studio (PWA Studio).
exl-id: 692eeafa-9289-4d66-9f2f-1e0fe36e681d
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# PWA Studio: Webpack låser sig innan kompileringen påbörjas

I den här artikeln beskrivs en föreslagen lösning för när ett javascript [Webpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack) låser sig länge innan kompileringen i Progressive Web App Studio (PWA Studio) börjar.

## Berörda produkter och versioner

* PWA Studio

## Problem

[Kontrollera vilken senaste version av pwa-buildpack som är &#x200B;](https://github.com/magento/pwa-studio/tree/master/packages/pwa-buildpack) och

```yaml
pwa-buildpack
```

versionsnumret står bredvid `package.json`-filnamnslistan. Om du har en gammal version av

```yaml
pwa-buildpack
```

-projektet kan webbpaketet vara låst under en lång tid innan kompileringen påbörjas.

<u>Steg som ska återskapas</u>:

<u>Förutsättningar</u>: Konfigurera en PWA Studio-butik, till exempel Venia, med en lokal Adobe Commerce-instans och kör en

```yaml
build
```

eller

```yaml
watch
```

-kommando.

<u>Förväntat resultat</u>:

* Om du använder    ```yaml    build    ```    genererar det standardartefakter för Venia.
* Om du använder    ```yaml    watch    ```    startar den Venia-butiken normalt.

<u>Faktiskt resultat</u>:

Dina

```yaml
build
```

eller

```yaml
watch
```

-kommandot kommer inte att slutföras och inte heller visas några fel.

## Lösningar

Uppdatera projektet med följande kommando:

```yaml
yarn upgrade
```

Kontrollera att du har en aktuell version av opensler på datorn med följande kommando:

```yaml
openssl version
```

Versionen ska vara 1.0 eller högre (eller LibreSSL 2, i fallet OSX High Sierra.).

Du kan installera senare versioner av OpenSSL med [Homebrew](https://brew.sh/) i OSX, [Chocolatey](https://chocolatey.org/) i Windows eller med Linux-distributionens pakethanterare.

## Relaterad läsning

* [JavaScript-webbpaket: begrepp](https://webpack.js.org/concepts/)
* [Inställningar för Venedig storefront](https://magento.github.io/pwa-studio/venia-pwa-concept/setup/)
* [PWA Buildpack](https://magento.github.io/pwa-studio/pwa-buildpack/)
* [kommandoradsgränssnitt för buildpack](https://magento.github.io/pwa-studio/pwa-buildpack/reference/buildpack-cli/)
* [Verktyg och bibliotek: buildpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack)
