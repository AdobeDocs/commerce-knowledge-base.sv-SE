---
title: Manuell orderexport till MOM misslyckas. Knappen Exportera ordning returnerar HTTP 404-fel
description: I den här artikeln beskrivs hur du åtgärdar ett problem, där ett försök att exportera en order till Magento Order Management (MOM) genom att klicka på knappen **Exportera order** i ordervyn i Commerce Admin returnerar felet " *404 Sidan hittades inte*".
exl-id: 75741473-7c9a-4418-a56f-de75ac246d27
feature: Data Import/Export
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Manuell orderexport till MOM misslyckas. Knappen Exportera ordning returnerar HTTP 404-fel

I den här artikeln beskrivs hur du åtgärdar ett problem, där du försöker exportera en order till Magento Order Management genom att klicka på **Exportordning** i ordervyn i Commerce Admin returnerar en *404 Sidan hittades inte* &quot;-fel.

## Berörda produkter och versioner

* Adobe Commerce 2.2.x, 2.3.x
* MOM Connector 2.3.0, 2.4.0, 3.2.0, 3.3.0

## Problem

<u>Steg som ska återskapas:</u>:

1. Klicka på Commerce Admin **Försäljning > Beställningar**.
1. Klicka på **Skapa ny order** -knappen.
1. Välj en användare, lägg till ett eller flera objekt, välj betalnings- och leveransmetoder och klicka sedan på knappen **Skicka beställning** -knappen.
1. Klicka på **Exportordning** och sedan **OK**.

<u>Förväntat resultat</u>:

Ordern skickas till MOM.

<u>Faktiskt resultat</u>:

A &quot; *404 Fel: Sidan hittades inte* visas.

## Lösning

* Uppgradera MOM Connector till 3.4.0 för Adobe Commerce 2.3.x eller MOM Connector 2.5 för Adobe Commerce 2.2.x.
* Om du inte kan uppgradera MOM-kopplingen kan du exportera beställningen till Magento Order Management med CLI-kommandot:

```bash
$bin/magento oms:orders:sync
```

## Relaterad läsning

[Teknisk dokumentation för Magento Order Management](https://omsdocs.magento.com/en/)
