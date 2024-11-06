---
title: Stock-statusen är felaktig efter installation av Inventory management
description: I den här artikeln finns en korrigering som anger att Stock-statusen är felaktig efter installation/uppgradering av Inventory management.
exl-id: ae32fbe3-deab-4f31-b427-95f8b54a476f
feature: Install, Inventory, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Stock-statusen är felaktig efter installation av Inventory management

I den här artikeln finns en korrigering som anger att Stock-statusen är felaktig efter installation/uppgradering av Inventory management.

## Stock-statusen är felaktig på vissa webbplatser

När du först installerat eller uppgraderat för att ha Inventory management i Adobe Commerce-miljön för flera webbplatser har inte alla webbplatser rätt Stock-status för produkter.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen, alla versioner, med Inventory management installerat
* Adobe Commerce lokal 2.3.0 och senare, med Inventory management installerat
* Magento Open Source 2.3.0 och senare, med Inventory management installerat

## Orsak

När du först installerar/uppgraderar tilldelas alla produkter standardkällan och alla kvantiteter kopplas till den källan. Standardwebbplatsen för Source tilldelas standardversionen av Stock, där standardwebbplatsen är associerad.

## Lösning

Om du har fler än en webbplats måste du lägga till dessa webbplatser som Sales Channeler i standardlagret eller andra anpassade resurser.

Se avsnittet [Stock i wiki-/användarhandboken](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-manage) i vår användarhandbok för mer information om hur du gör detta.
