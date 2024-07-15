---
title: Extension Manager visar inga tillägg i Adobe Commerce 2.3.x
description: I den här artikeln finns en lösning på problemet med saknade tillägg i Admin Extension Manager i Adobe Commerce 2.3.x när du har köpt tillägg via Commerce Marketplace.
exl-id: bed8506d-39b9-449a-891b-466d214a0fe8
feature: Extensions
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Extension Manager visar inga tillägg i Adobe Commerce 2.3.x

I den här artikeln finns en lösning på problemet med saknade tillägg i Admin Extension Manager i Adobe Commerce 2.3.x när du har köpt tillägg via Commerce Marketplace.

## Berörda produkter och versioner

* Adobe Commerce version (alla distributionsmetoder) 2.3.x

## Problem

När du köper tillägg via Commerce Marketplace kan du inte installera dem med Adobe Commerce Extension Manager. När du lägger till dina nycklar och synkroniserar till Marketplace visas inga tillägg i Extension Manager.

**Tillfällig lösning** för problemet är att använda kommandoradsinstallationen av Adobe Commerce enligt [den allmänna CLI-installationen](https://devdocs.magento.com/extensions/install/) i utvecklardokumentationen.

<u>Steg som ska återskapas</u>:

1. Köp ett tillägg via Commerce Marketplace.
1. Lägg till tilläggets nycklar och synkronisera till Marketplace.
1. Gå till administratörens Extension Manager.

<u>Förväntat resultat</u>:

Tillägget visas Extension Manager i Commerce Admin.

<u>Faktiskt resultat</u>:

**Inget tillägg visas i sektionen Extension Manager i Commerce Admin, som liknar bilden nedan:**


![KB-607_Image_1.png](assets/KB-607_Image_1.png)

## Tillfällig lösning

Använd kommandoradsinstallationen av Adobe Commerce så som visas i [Allmän CLI-installation](https://devdocs.magento.com/extensions/install/) i utvecklardokumentationen.
