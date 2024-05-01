---
title: "FEL: Det gick inte att starta Adobe Commerce på molninfrastruktur"
description: "Den här artikeln innehåller en lösning för när sidcachen värms upp och misslyckas med ett fel:"
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# FEL: Det gick inte att värma på Adobe Commerce i molninfrastruktur

Den här artikeln innehåller en lösning för när sidcachen värms upp och misslyckas med ett fel:

*FEL: Uppvärmningen misslyckades:`<website link>`*

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen, alla [versionerna](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Cacheuppvärmningen misslyckades.

<u>Steg som ska återskapas</u>:

Starta cacheuppvärmningsåtgärder.

<u>Förväntat resultat</u>:

Sidor eller hela platsen läses in.

<u>Faktiskt resultat</u>:

Webbplatsen är inte tillgänglig eller så är svarstiden för hög. *FEL: Uppvärmningen misslyckades:`<website link>`*

## Orsak

Cachevärmen fungerar inte med HTTP-åtkomstkontroll aktiverad.

## Lösning

Kontrollera att du inte har åtkomstkontroll aktiverad: gå till den specifika grenen/miljön och klicka på **Inställningar** och kontrollera **HTTP-åtkomstkontroll** inställning - cacheuppvärmning kan inte inträffa i det här scenariot och åtkomstkontroll måste inaktiveras.

## Relaterad läsning

* [Adobe Commerce User Guide > Full Page Cache](https://docs.magento.com/user-guide/system/cache-full-page.html) i vår användarhandbok.
* [Cacheuppvärmning och webbplatsen är inte tillgänglig i Adobe Commerce](/help/troubleshooting/miscellaneous/cache-warming-up-and-site-unavailable-on-magento.md) i vår kunskapsbas för support.
