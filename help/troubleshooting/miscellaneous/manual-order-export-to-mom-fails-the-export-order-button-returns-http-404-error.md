---
title: Manuell orderexport till MOM misslyckas. Knappen Exportera ordning returnerar HTTP 404-fel
description: I den här artikeln beskrivs hur du åtgärdar ett problem, där ett försök att exportera en order till Magento Order Management (MOM) genom att klicka på knappen **Exportera order** i ordervyn i Commerce Admin returnerar felet " *404 Sidan hittades inte*".
exl-id: 75741473-7c9a-4418-a56f-de75ac246d27
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Manuell orderexport till MOM misslyckas. Knappen Exportera ordning returnerar HTTP 404-fel

I den här artikeln beskrivs hur du åtgärdar ett problem, där ett försök att exportera en order till Magento Order Management (MOM) genom att klicka på knappen **Exportera ordning** i ordervyn i Commerce Admin returnerar felet *404 Sidan hittades inte* .

## Berörda produkter och versioner

* Adobe Commerce 2.2.x, 2.3.x
* MOM Connector 2.3.0, 2.4.0, 3.2.0, 3.3.0

## Problem

<u>Steg som ska återskapas:</u>:

1. Klicka på **Försäljning > Beställningar** i Commerce Admin.
1. Klicka på knappen **Skapa ny ordning** .
1. Välj en användare, lägg till ett eller flera objekt, välj betalnings- och leveransmetoder och klicka sedan på knappen **Skicka beställning** .
1. Klicka på knappen **Exportordning** och sedan på **OK**.

<u>Förväntat resultat</u>:

Ordern skickas till MOM.

<u>Faktiskt resultat</u>:

Sidan *404 Fel: Sidan hittades inte* visas.

## Lösning

* Uppgradera MOM Connector till 3.4.0 för Adobe Commerce 2.3.x eller MOM Connector 2.5 för Adobe Commerce 2.2.x.
* Om du inte kan uppgradera MOM-kopplingen kan du exportera beställningen till Magento Order Management med CLI-kommandot:

```bash
$bin/magento oms:orders:sync
```

## Relaterad läsning

[Teknisk Magento Order Management](https://commerce-docs.github.io/oms-documentation-archive/)
