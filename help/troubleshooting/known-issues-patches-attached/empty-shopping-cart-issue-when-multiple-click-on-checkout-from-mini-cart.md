---
title: Tomt kundvagnsproblem när du klickar flera gånger på kassan från mini cart
description: I den här artikeln finns en patch för ett känt problem med Adobe Commerce 2.2.3 som beror på att en kundvagn är tom efter att man klickat på **Gå till kassan** flera gånger i kundvagnen.
exl-id: 06b82c91-8998-4e7b-9fc0-671c9b2a2d3f
feature: Checkout, Orders, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# Tomt kundvagnsproblem när du klickar flera gånger på kassan från mini cart

I den här artikeln finns en korrigeringsfil för ett känt Adobe Commerce 2.2.3-problem som rör en kundvagn som är tom efter att kunderna har klickat på **Gå till kassan** flera gånger i minikundvagnen.

## Problem

Kunder lägger till produkter i kundvagnen, försöker checka ut genom att klicka på knappen **Gå till kassan** flera gånger, men när de går till kundvagnen är kundvagnen tom. Minivagnen kan fortfarande visa produkter.

<u>Steg som ska återskapas</u> :

1. Öppna en produktsida i butiken.
1. Lägg produkter i kundvagnen.
1. Klicka **Gå till kassan** flera gånger i den lilla kundvagnen.

<u>Förväntat resultat</u> :

Kundvagnen innehåller alla produkter du har lagt till.

<u>Faktiskt resultat</u> :

Du har inga artiklar i kundvagnen.

## Lappa

Patcherna är kopplade till den här artikeln. Om du vill hämta en patch rullar du nedåt till slutet av artikeln och klickar på önskat filnamn eller klickar på någon av följande länkar:

[Ladda ned MDVA-10441\_EE\_2.2.3\_v3.comser.patch](assets/MDVA-10441_EE_2.2.3_v3.composer.patch.zip)

[Hämta MDVA-17078\_EE\_2.2.5\_COMPOSER\_v1.patch](assets/MDVA-17078_EE_2.2.5_COMPOSER_v1.patch.zip)

### Kompatibla Adobe Commerce-versioner

Patcharna skapades för:

* Adobe Commerce lokal 2.2.3 (filen `MDVA-10441_EE_2.2.3_v3.composer.patch`)
* Adobe Commerce i molninfrastruktur 2.2.5 (`MDVA-17078_EE_2.2.5_COMPOSER_v1.patch` fil)

Korrigeringen `MDVA-10441_EE_2.2.3_v3.composer.patch` är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce på molninfrastrukturversioner från 2.2.1 till 2.2.5
* Adobe Commerce lokala versioner från 2.2.1 till 2.2.5

Korrigeringen `MDVA-17078_EE_2.2.5_COMPOSER_v1.patch` är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce 2.2.5

## Så här lägger du på en patch

Instruktioner finns i [Använda en dispositionsruta från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.

## Bifogade filer
