---
title: "Adobe Commerce 2.4.2 B2B: Rabatten ändras fortfarande på lönesätt"
description: I den här artikeln beskrivs ett känt Adobe Commerce 2.4.2 B2B-problem där en rabatt som är knuten till betalningsmetoden kvarstår efter en ändring av betalningsmetod vid utcheckning. Det finns för närvarande ingen upplösning.
exl-id: cd863852-403b-404f-8717-c78c238f5f33
feature: B2B, Orders, Payments, Personalization
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Adobe Commerce 2.4.2 B2B: Rabatten är fortfarande en lönemetodändring

I den här artikeln beskrivs ett känt Adobe Commerce 2.4.2 B2B-problem där en rabatt som är knuten till betalningsmetoden kvarstår efter en ändring av betalningsmetod vid utcheckning. Det finns för närvarande ingen upplösning.

## Berörda produkter och versioner

* Adobe Commerce 2.4.2
* Adobe Commerce i molninfrastruktur 2.4.2
* B2B för Adobe Commerce 1.3.1


## Problem

<u>Steg som ska återskapas</u> :

1. Skapa en kundvagn **Prisregel** som är knuten till en betalningsmetod (Exempel: PayPal-användare får en rabatt på 20 %.)
1. Skapa en inköpsorder (PO) och välj PayPal som betalningsmetod. Rabatten tillämpas.
1. PO har godkänts.
1. Gå till betalningssidan för att slutföra ordern.
1. Välj en annan betalningsmetod.

<u>Faktiska resultat</u> :

Betalningsmetodens rabatt gäller fortfarande för ordersumman.  Inget felmeddelande visas.Butiksägaren kan se att detta har inträffat genom att kontrollera orderhistoriken.

<u>Förväntade resultat</u>: Betalningsmetodrabatten tas bort från ordersumman som förväntat.

## Lösning

Det finns för närvarande ingen upplösning.
