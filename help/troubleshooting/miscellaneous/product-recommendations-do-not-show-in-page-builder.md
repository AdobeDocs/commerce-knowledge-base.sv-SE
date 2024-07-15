---
title: Produkt-Recommendations visas inte i Page Builder
description: Den här artikeln innehåller en lösning på problemet där Recommendations-alternativet Product inte visas i Page Builder.
exl-id: e96a446b-2e64-47a6-ac1b-e73183da9fb8
feature: Page Builder, Configuration, Personalization, Products, Recommendations
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Produkt-Recommendations visas inte i Page Builder

Den här artikeln innehåller en lösning på problemet där Recommendations-alternativet Product inte visas i Page Builder.

## Berörda produkter och versioner

* Adobe Commerce (alla distributionsmetoder)

## Problem

Alternativet Product Recommendations visas inte i Page Builder.

## Orsak

Det finns inget alternativ i Page Builder för att lägga till Product Recommendations. Produkt-Recommendations för Page Builder är en valfri modul som installeras separat.

## Lösning

1. Kontrollera om du har installerat modulen separat genom att köra kommandot: `composer show magento/module-page-builder-product-recommendations`
1. Om det returnerar följande meddelande: *Package magento/module-page-builder-product-recommendations not found* måste du installera det genom att köra kommandot: `composer require magento/module-page-builder-product-recommendations`

Genom att aktivera Product Recommendations i Page Builder kan du [lägga till en rekommendationsenhet](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) i allt innehåll som skapas i Page Builder.

## Relaterad läsning

* [Lägg till innehåll - Produkt-Recommendations](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) i vår användarhandbok.
* [Installera och konfigurera Recommendations](https://devdocs.magento.com/recommendations/install-configure.html) i utvecklardokumentationen.
* [Adobe Commerce Användarhandbok](https://docs.magento.com/user-guide/)
