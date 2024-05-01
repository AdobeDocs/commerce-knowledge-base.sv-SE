---
title: MySQL-tabeller är för stora
description: I den här artikeln beskrivs varför det är ett problem när en MySQL-tabell blir större än 1 GB och hur du förhindrar detta.
exl-id: 43f74e3b-7f2e-428c-9964-56d2ce98a34d
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# MySQL-tabeller är för stora

I den här artikeln beskrivs varför det är ett problem när en MySQL-tabell blir större än 1 GB och hur du förhindrar detta.

## Berörda produkter och versioner:

* Adobe Commerce i molninfrastruktur 2.x.x
* Adobe Commerce lokal 2.x.x

## Problem

Storleken på MySQL-tabeller påverkar inte platsens prestanda direkt. Om en tabell är stor innebär det dock att det finns många infogningsåtgärder i den här tabellen, med eventuella extra data eller inaktuella data. MySQL är utformat för databaser, där förhållandet mellan läs- och skrivåtgärder är 80 %/20 %.  För stora tabeller, 1 GB och mer, kan MySQL-index, som är utformade för att öka prestanda vid läsåtgärder, försämra prestanda vid skrivåtgärder.

## Lösning

Tänk på följande alternativ för att undvika prestandaförsämring:

* Skapa CRON-jobb som rensar upp stora tabeller. Se [Söka efter stora MySQL-tabeller](/help/how-to/general/find-large-mysql-tables.md) i vår kunskapsbas för support om rekommendationer om hur du identifierar stora tabeller.
* För tabeller som är större än 1 GB använder du en MySQL-motor som är optimerad för att skriva loggar. Exempel: Arkivmotorn.
* Uppdatera funktionaliteten för att undvika att lagra loggar i DB.

## Relaterad läsning

[Överdimensionerade ändringsloggtabeller orsakar förseningar i enhetsuppdateringar](/help/troubleshooting/database/changes-in-the-database-are-not-reflected-on-the-storefront.md) i vår kunskapsbas för support.
