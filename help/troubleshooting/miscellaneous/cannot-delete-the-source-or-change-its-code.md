---
title: Kan inte ta bort källan eller ändra dess kod
description: I den här artikeln finns en korrigering för när du inte kan ta bort en källa helt och/eller ändra dess kod.
exl-id: dbdb4d62-9138-4a3d-a58f-8671f1dc5b42
feature: Console
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Kan inte ta bort källan eller ändra dess kod

I den här artikeln finns en korrigering för när du inte kan ta bort en källa helt och/eller ändra dess kod.

## Problem

Källor kan inte tas bort oavsett produkttilldelning.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen (alla versioner), med Magento Inventory installerad
* Adobe Commerce lokal 2.3.0 och senare med Magento Inventory installerad
* Magento Open Source 2.3.0 och senare med Magento Inventory installerad

## Orsak

Det är inte möjligt att helt ta bort en källa och/eller ändra dess kod.

Om du tar bort en källa helt och hållet uppstår problem med orderdata eftersom källorna är en del av produktinventeringar, order, leveransdata och mycket annat.

Koden är viktig för att koppla källan till beställningarna. Detta är ett unikt ID för källan och är inaktiverat för redigering.

## Lösning

Du kan ta bort en källa från en produkt genom att överföra lagret eller släppa produkten från alla leveranser på en plats.

Om du behöver ta bort en källa från [SSA](https://experienceleague.adobe.com/sv/docs/commerce-admin/inventory/basics/selection-reservations)-beräkningar och Adobe Commerce Inventory-orderbearbetning kan du inaktivera källan. Inaktiverade källor bevarar alla data, tilldelade produkter och lagerkvantiteter och kan återaktiveras när som helst för att börja leverera igen.

Mer information om hur du inaktiverar en källa finns i guiden [Skapa källor](https://github.com/magento/inventory/wiki/Create-Sources#disable-sources).
