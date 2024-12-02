---
title: 'FEL: Det gick inte att värma på Adobe Commerce i molninfrastruktur'
description: 'Den här artikeln innehåller en lösning för när sidcachen värms upp och misslyckas med ett fel:'
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# FEL: Det gick inte att värma på Adobe Commerce i molninfrastruktur

Den här artikeln innehåller en lösning för när sidcachen värms upp och misslyckas med ett fel:

*FEL: Uppvärmningen misslyckades:`<website link>`*

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen, alla [versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

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

Kontrollera att du inte har åtkomstkontroll aktiverad: gå till den specifika grenen/miljön och klicka på ikonen **Inställningar** och kontrollera inställningen **HTTP-åtkomstkontroll** - det går inte att värma cachen i det här scenariot och åtkomstkontrollen måste inaktiveras.

## Relaterad läsning

* [Adobe Commerce Användarhandbok > Helsidescache](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#full-page-caching) i vår användarhandbok.
* [Cacheuppvärmning och webbplatsen är inte tillgänglig på Adobe Commerce](/help/troubleshooting/miscellaneous/cache-warming-up-and-site-unavailable-on-magento.md) i vår kunskapsbas för support.
