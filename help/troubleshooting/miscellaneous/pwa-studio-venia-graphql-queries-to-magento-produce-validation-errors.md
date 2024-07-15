---
title: "PWA Studio: Venia GraphQL frågar efter Adobe Commerce vid valideringsfel"
description: I den här artikeln ges rekommendationer om hur du löser problemet där Venia storefront GraphQL skickar frågor till Adobe Commerce-instansen som genererar valideringsfel.
exl-id: ba268945-2a10-4af5-8089-cde21f0687bd
feature: GraphQL
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# PWA Studio: Venia GraphQL-frågor till Adobe Commerce skapar valideringsfel

I den här artikeln ges rekommendationer om hur du löser problemet där Venia storefront GraphQL skickar frågor till Adobe Commerce-instansen som genererar valideringsfel.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.2.x, 2.3.x
* Adobe Commerce om molninfrastruktur 2.2.x, 2.3.x
* PWA Studio-projekt för Adobe Commerce

## Problem

Venia GraphQL-frågor till Adobe Commerce lokalt eller Adobe Commerce i molninfrastruktur ger upphov till valideringsfel.

## Orsak

En av orsakerna till problemet kan vara Venia och dess GraphQL-frågor är inte synkroniserade med schemat för den anslutna Adobe Commerce-instansen.

## Lösning

Om du vill testa om dina frågor är aktuella kör du följande kommando i projektets rot:

```bash
yarn run validate-queries
```

Då visas en kompatibilitetsrapport. Om du har inkompatibiliteter måste du uppgradera din PWA Studio eller Adobe Commerce-instans. Kontrollera [kompatibilitetsmatrisen för Adobe Commerce](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/version-compatibility/) för att se exakt vilka versioner du behöver.

Se följande dokumentation för instruktioner om hur du uppgraderar:

* Om du vill uppgradera till PWA Studio söker du efter avsnittet Uppgradera från en tidigare version i [PWA versionsinformation](https://github.com/magento/pwa-studio/releases/) för den version du behöver uppgradera till.
* [Uppgradera Adobe Commerce på molninfrastrukturversion](https://devdocs.magento.com/cloud/project/project-upgrade.html) i utvecklardokumentationen
* [Uppgradera Adobe Commerce lokalt (installeras med&quot;create-project&quot; eller arkiv för disposition&quot;)](https://devdocs.magento.com/guides/v2.3/comp-mgr/cli/cli-upgrade.html) i utvecklardokumentationen
* [Uppgradera Adobe Commerce lokalt (installeras genom kloning av Adobe Commerce repo)](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/dev_update-magento.html) i utvecklardokumentationen

## Relaterad läsning

* [PWA Studio: Webpack låser sig innan kompileringen börjar](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md) i vår kunskapsbas för support
* [PWA Studio: Valideringsfel när utvecklarläge körs](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md) i vår kunskapsbas för support
* [PWA Studio: Webbläsaren visar&quot;Kan inte proxyvisa&quot;-fel](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md) i vår kunskapsbas för support
* [Konfigurera NPM så att PWA Studio](/help/how-to/general/configure-npm-to-be-able-to-use-pwa-studio.md) kan användas i vår kunskapsbas för support
* [PWA för Adobe Commerce-dokumentation](https://magento.github.io/pwa-studio/)
