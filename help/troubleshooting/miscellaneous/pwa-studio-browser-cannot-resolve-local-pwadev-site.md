---
title: 'PWA Studio: webbläsaren kan inte matcha .local.pwadev-platsen'
description: Den här artikeln innehåller en lösning för när ett annat program eller en process har redigerat din [värdfil](https://en.wikipedia.org/wiki/Hosts_(file)) och tagit bort posten för din projektdomän.
exl-id: a1606016-906a-433f-9e40-9faa5f9bd790
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# PWA Studio: webbläsaren kan inte matcha .local.pwadev-platsen

Den här artikeln innehåller en lösning för när ett annat program eller en annan process har redigerat din [värdfil](https://en.wikipedia.org/wiki/Hosts_(file\)) och tagit bort posten för din projektdomän.

## Berörda produkter och versioner

PWA Studio för Adobe Commerce

## Problem

När du bläddrar till webbplatsen dev/staging kan du inte se webbplatsen `.local.pwadev`.

## Orsak

Med PWA Studio kan du tilldela din lokala dator ett eget värdnamn och SSL-certifikat för ditt projekt. Detta innebär att du skapar en ny post i datorns värdfil som ser ut ungefär som `my-storefront-project-abc123.local.pwadev`.

Den här posten talar om för alla webbläsare på utvecklarens dator att titta på det lokala butiksprojektet när de öppnar den URL:en. Om ett annat program eller en annan process kom in och tog bort posten, skulle webbläsaren inte veta vart den skulle gå och webbläsaren kan inte matcha webbplatsen `.local.pwadev`.

## Lösning

Du kan [redigera din värdfil](https://support.rackspace.com/how-to/modify-your-hosts-file/) manuellt om du vill lägga till posten igen, men du bör undersöka ditt andra installerade program för att se vad som har skrivit över den tidigare ändringen.

## Relaterad läsning i vår kunskapsbas

* [PWA Studio: Självsignerat certifikatförtroendefel](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio: Webpack låser sig innan kompileringen påbörjas](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio: Felet &quot;Kan inte proxyvisa&quot; visas i webbläsaren](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio: Valideringsfel när utvecklarläget körs](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
