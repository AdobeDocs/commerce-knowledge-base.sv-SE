---
title: Problem efter att en modul har inaktiverats
description: I den här artikeln finns en lösning på problem med modulfunktioner efter att modulutdata har inaktiverats i Commerce Admin.
exl-id: 517f6993-f09e-4a94-8c57-175ecf9a98a8
feature: Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

När du har inaktiverat modulutdata i Commerce Admin, under **Lager** > **Inställningar** > **Konfiguration** > ADVANCED > **Avancerat**, kan du börja se problem med modulfunktionen.

## Orsak

Om du inaktiverar en modulutdata under **Lagrar** > **Inställningar** > **Konfiguration** > AVANCERAT > **Avancerat** inaktiveras bara utdata (HTML, JS), men funktionen för den här modulen inaktiveras inte.

## Lösning

Om du behöver inaktivera modulfunktioner inaktiverar du modulen enligt beskrivningen i [Aktivera eller inaktivera moduler](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/tutorials/manage-modules) i utvecklardokumentationen.

Funktionen för inaktivering av modulutdata har tagits bort från version 2.2.0.
