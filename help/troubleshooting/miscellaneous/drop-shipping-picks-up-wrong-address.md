---
title: Felaktig adress för leverans hämtas
description: Leveranslösningen hittar inte adressen till produktens källa.
exl-id: ce89713f-d506-4e4f-bf49-cdee3e6d29b5
feature: Customer Service, Orders, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# Felaktig adress för leverans hämtas

## Problem

Leveranslösningen hittar inte adressen till produktens källa.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen (alla versioner), med Magento Inventory installerad
* Adobe Commerce lokal 2.3.0 och senare med Magento Inventory installerad
* Magento Open Source 2.3.0 och senare med Magento Inventory installerad

### Orsak

Magento Inventory stöder för närvarande inte beräkning av fraktkostnader baserat på källadressen vid utcheckningen. I stället används standardbutiksadressen från konfigurationen i alla fall.

## Relaterad läsning

* [Vanliga frågor om Magento-inventering](https://github.com/magento/inventory/wiki/MSI-FAQs) i GitHub.
