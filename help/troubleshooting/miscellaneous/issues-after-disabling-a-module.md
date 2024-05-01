---
title: Problem efter att en modul har inaktiverats
description: I den här artikeln finns en lösning på problem med modulfunktioner efter att modulutdata har inaktiverats i Commerce Admin.
exl-id: 517f6993-f09e-4a94-8c57-175ecf9a98a8
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---

# Problem efter att en modul har inaktiverats

I den här artikeln finns en lösning på problem med modulfunktioner efter att modulutdata har inaktiverats i Commerce Admin.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur 2.1.X eller tidigare
* Adobe Commerce lokal 2.1.X eller tidigare

## Problem

Har inaktiverat modulutdata i Commerce Admin, under **Lager** > **Inställningar** > **Konfiguration** > AVANCERAT > **Avancerat** kan du kanske börja se problem med modulfunktionen.

## Orsak

Inaktivera modulutdata under **Lager** > **Inställningar** > **Konfiguration** > AVANCERAT > **Avancerat** inaktiverar bara utdata (HTML, JS), men funktionen i den här modulen inaktiveras inte.

## Lösning

Om du behöver inaktivera modulfunktionen inaktiverar du modulen enligt beskrivningen i [Aktivera eller inaktivera moduler](https://devdocs.magento.com/guides/v2.1/install-gde/install/cli/install-cli-subcommands-enable.html) i vår dokumentation för utvecklare.

Funktionen för inaktivering av modulutdata har tagits bort från version 2.2.0.
