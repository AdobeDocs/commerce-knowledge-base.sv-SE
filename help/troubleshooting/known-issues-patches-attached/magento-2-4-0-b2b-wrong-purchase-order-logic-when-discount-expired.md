---
title: "Adobe Commerce 2.4.0 B2B: fel inköpsorderlogik när rabatten går ut"
description: I den här artikeln finns en patch för den kända utgåvan av en inköpsorderrabatt som inte gäller i Adobe Commerce 2.4.0 B2B. Om inköpsordern fick en rabattkod som gick ut medan inköpsordern var i godkännandeprocessen, återspeglar den godkända ordern inte rabatten.
exl-id: 3ef41655-c31e-4e9c-8985-fa1b4fd53170
feature: B2B, Orders, Payments, Personalization, Purchase Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 B2B: fel inköpsorderlogik när rabatten gått ut

I den här artikeln finns en patch för den kända utgåvan av en inköpsorderrabatt som inte gäller i Adobe Commerce 2.4.0 B2B. Om inköpsordern fick en rabattkod som gick ut medan inköpsordern var i godkännandeprocessen, återspeglar den godkända ordern inte rabatten.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.4.0
* Adobe Commerce lokal 2.4.0

## Problem

<u>Förutsättningar</u>: en rabattkupong skapas och godkännanderegler som förhindrar att inköpsordrar bearbetas automatiskt finns.

<u>Steg som ska återskapas:</u>

1. Placera en inköpsorder med rabatt.
1. Inaktivera rabattkupongen.
1. Godkänn inköpsorder som chef.
1. Kontrollera den ordning som skapats som resultat.

<u>Förväntat resultat:</u>

Ordern skapas med en diskonterad summa.

<u>Faktiskt resultat:</u>

Ordern skapas för hela beloppet.

## Lösning

Använd den patch som finns i den här artikeln.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[B2B-709-composer.patch](assets/B2B-709-composer.patch.zip)

Programfixen kan också laddas ned i `.git` och `.composer` , format på [Adobe Commerce Downloads](https://magento.com/tech-resources/download) sida, under **Patchar** i den vänstra kolumnnavigeringen. Sök efter XXX korrigeringsfiler.

## Så här sätter du på plåstret

Se [Använda en kompositkorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support för instruktioner.
