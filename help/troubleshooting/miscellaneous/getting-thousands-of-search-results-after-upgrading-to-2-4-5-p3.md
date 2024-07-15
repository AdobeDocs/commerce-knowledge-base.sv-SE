---
title: Få tusentals resultat när du letar efter en viss produkt
description: Den här artikeln innehåller en lösning på problemet där du får tusentals sökresultat när du söker efter en viss produkt.
feature: Quotes, Search, Returns
role: Developer, Admin
exl-id: 0eccf212-96be-4ea5-9e6e-95f27d7d9f92
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Få tusentals resultat när du letar efter en viss produkt

I den här artikeln finns en lösning på ett problem där du får tusentals sökresultat när du söker efter en viss produkt.

## Berörda produkter och versioner

* Adobe Commerce alla versioner med [!DNL ElasticSearch] installerade

## Problem

Du söker efter en viss produkt (till exempel *WSH12-32-Red*) men sökningen returnerar många liknande produkter.

## Lösningar

Typen av fulltextsökning i [!DNL ElasticSearch] baseras på relevans, inte på exakt matchning. Därför ordnas de mest relevanta matchningarna (som exakt matchade SKU:er) först.

Om du behöver ett sökresultat som matchar exakt söktermen (exakt matchning) bör du använda citattecken för sökfrågan. Om du till exempel frågar efter *WSH12-32-Red* utan citattecken returneras flera resultat med den exakta matchningen (produkten *SKU WSH12-32-Red*) visas först i resultatet. Men den citerade frågan *WSH12-32-Red* returnerar bara ett exakt matchningsresultat.
