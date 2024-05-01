---
title: "Adobe Commerce 2.4.2 B2B: E-postmallen uppdateras inte"
description: I den här artikeln beskrivs ett känt Adobe Commerce 2.4.2 B2B-problem där uppdateringen av viss information i en e-postmall inte uppdateras i e-postmeddelanden. Detta berör e-postinnehåll som kundinformation, valutakurser, valutasymbol, ändring av e-postmall osv. Det finns för närvarande ingen lösning, men det finns en lösning längst ned i den här artikeln.
exl-id: 31b7086f-a941-4682-aa07-301ac31d543b
feature: B2B, Communications
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Adobe Commerce 2.4.2 B2B: E-postmallen uppdateras inte

I den här artikeln beskrivs ett känt Adobe Commerce 2.4.2 B2B-problem där uppdateringen av viss information i en e-postmall inte uppdateras i e-postmeddelanden. Detta berör e-postinnehåll som kundinformation, valutakurser, valutasymbol, ändring av e-postmall osv. Det finns för närvarande ingen lösning, men det finns en lösning längst ned i den här artikeln.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.4.2
* Adobe Commerce molninfrastruktur 2.4.2
* B2B 1.3.1

## Problem

<u>Steg som ska återskapas</u>:

1. Företagsadministratör skapar en inköpsorder i förgrunden.
1. Kontrollera e-postmeddelandet om automatiskt godkänd. The **kundnamn** / **valutakurs** bör vara förväntade värden.
1. Ändra valutasymbol (**Stores > Configuration > Currency Setup > Currency Options**) i administratörens och företagets administratörsnamn på kundkontosidan.
1. Kundadministratör skapar en annan inköpsorder i Admin.
1. Kontrollera e-postmeddelandet om automatiskt godkänd.

<u>Förväntade resultat:</u>

Kundens namn och valutasymbol ändras i e-postmeddelanden och får sina nya värden som förväntat.

<u>Faktiska resultat</u>:

Kundens namn och valutasymbol ändras inte i e-postmeddelanden och har sina tidigare värden.

## Tillfällig lösning

Kör cron-jobbet eller konsumenten manuellt för att sprida den nya informationen.

## Relaterad läsning

* [Hantera meddelandeköer](https://devdocs.magento.com/guides/v2.4/config-guide/mq/manage-message-queues.html) i vår dokumentation för utvecklare.
