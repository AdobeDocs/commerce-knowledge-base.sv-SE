---
title: '[!DNL MySQL] tabeller är för stora'
description: I den här artikeln beskrivs varför det är ett problem när en  [!DNL MySQL] tabell blir större än 1 GB och hur du förhindrar detta.
exl-id: 43f74e3b-7f2e-428c-9964-56d2ce98a34d
feature: Services
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# [!DNL MySQL] tabeller är för stora

I den här artikeln beskrivs varför det är ett problem när en [!DNL MySQL]-tabell blir större än 1 GB och hur du förhindrar detta.

## Berörda produkter och versioner:

* Adobe Commerce i molninfrastruktur 2.x.x
* Adobe Commerce lokal 2.x.x

## Problem

Tabellstorleken [!DNL MySQL] påverkar inte platsens prestanda direkt. Om en tabell är stor innebär det dock att det finns många infogningsåtgärder i den här tabellen, med eventuella extra data eller inaktuella data. [!DNL MySQL] är utformat för databaser, där förhållandet mellan läs- och skrivåtgärder är 80 %/20 %.  För stora tabeller, 1 GB eller mer, kan [!DNL MySQL] index, som är utformade för att öka prestanda vid läsåtgärder, försämra prestanda vid skrivåtgärder.

## Lösning

Tänk på följande alternativ för att undvika prestandaförsämring:

* Skapa CRON-jobb som rensar upp stora tabeller. Mer information om hur du identifierar stora tabeller finns i [Hitta stora [!DNL MySQL] tabeller](/help/how-to/general/find-large-mysql-tables.md) i vår kunskapsbas för support.
* För tabeller som är större än 1 GB använder du en [!DNL MySQL]-motor som är optimerad för att skriva loggar. Exempel: Arkivmotorn.
* Uppdatera funktionaliteten för att undvika att lagra loggar i DB.

## Relaterad läsning

* [Överdimensionerade ändringsloggtabeller orsakar fördröjningar i entitetsuppdateringar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/database/changes-in-the-database-are-not-reflected-on-the-storefront) i vår kunskapsbas för support
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
