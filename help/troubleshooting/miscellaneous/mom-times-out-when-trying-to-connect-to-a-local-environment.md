---
title: Magento Order Management System (OMS) för Adobe Commerce timeout
description: I den här artikeln finns en lösning på problemet där det inte går att registrera den lokalt installerade mikrotjänsten med MOM med hjälp av ngrok i Magento Order Management System (OMS) för Adobe Commerce, eftersom MOM-timeout uppstår vid återanrop.
exl-id: 19149d8c-ea24-46fb-8815-9f637afe46ca
feature: System
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Magento Order Management System (OMS) för Adobe Commerce timeout

I den här artikeln finns en lösning på problemet där det inte går att registrera den lokalt installerade mikrotjänsten med MOM med hjälp av ngrok i Magento Order Management System (OMS) för Adobe Commerce, eftersom MOM-timeout uppstår vid återanrop.

## Berörda produkter och versioner

* Adobe Commerce 2.3.1
* OMS
* ngrok

>[!WARNING]
>
>Ansvarsfriskrivning: Adobe Commerce rekommenderar eller stöder inte något särskilt verktyg för att upprätta tunnlar. Föregående är endast förslag. Mer information finns i [ngrok-dokumentationen](https://ngrok.com/docs).

## Problem

<u>Steg som ska återskapas</u>

1. Installera Adobe Commerce i den lokala miljön.
1. Skapa en tunnel för att visa den lokala servern.
1. Försök med att [ansluta till OMS](https://omsdocs.magento.com/en/integration/connector/setup-tutorial/).

<u>Förväntat resultat</u>

Anslutningen har upprättats.

<u>Faktiskt resultat</u>

MCOM verkar ha en timeout vid återanrop till webbadressen för webbadressen.

## Orsak

En av de möjliga orsakerna till timeout-problemet är att servrarna är geografiskt för långt borta och att anslutningen tar för lång tid.

## Lösning

Lägg till en parameter som anger ditt område när du startar grok. Så här:

```bash
./ngrok http 80 -region eu
```

Standardregionen är USA. Se [alla möjliga värden](https://ngrok.com/docs#config_region).
