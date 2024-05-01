---
title: Webbplatsen är i underhållsläge men tillgänglig för kunder
description: Den här artikeln innehåller en fix för när underhållsläge är aktiverat (ett problem med Adobe Commerce i molninfrastruktur), men butiken är fortfarande tillgänglig för kunder.
exl-id: 61b81fbd-a382-44b5-94e9-5b6d72f11349
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Webbplatsen är i underhållsläge men tillgänglig för kunder

Den här artikeln innehåller en fix för när underhållsläge är aktiverat (ett problem med Adobe Commerce i molninfrastruktur), men butiken är fortfarande tillgänglig för kunder.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur (alla versioner)

## Problem

<u>Steg som ska återskapas:</u>

1. Aktivera underhållsläget för platsen.
1. Navigera till butiken.

<u>Förväntat resultat:</u>

Underhållssidan visas.

<u>Faktiskt resultat:</u>

Fördelningssidor visas som vanligt.

## Orsak

Sidorna är fortfarande cachelagrade, så underhållssidan visas inte.

## Lösningen på platsen är synlig trots att den är i underhållsläge

1. SSH i din miljö.
1. Kör `php bin/magento cache:clean` -kommando.

## Relaterad läsning

[Aktivera eller inaktivera underhållsläge](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-maint.html) i vår dokumentation för utvecklare.
