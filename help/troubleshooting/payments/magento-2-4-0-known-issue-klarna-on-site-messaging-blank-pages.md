---
title: "Adobe Commerce 2.4.0 known issue: Klarna On-Site Messaging blank pages"
description: I den här artikeln beskrivs ett känt problem med betalningsmetoden Adobe Commerce 2.4.0, där aktivering av klarna på-plats-meddelanden utan att ange ett designtema resulterar i att produktsidor inte visas korrekt i butiken (produktsidor visas tomma).
exl-id: f0f9edfc-eaad-4947-9200-41e217bfbe84
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Klarna On-Site Messaging - tomma sidor

I den här artikeln beskrivs ett känt problem med betalningsmetoden Adobe Commerce 2.4.0, där aktivering av klarna på-plats-meddelanden utan att ange ett designtema resulterar i att produktsidor inte visas korrekt i butiken (produktsidor visas tomma).

## Berörda produkter och versioner

* Adobe Commerce lokal 2.4.0
* Adobe Commerce om molninfrastruktur 2.4.0

<u>Förutsättningar:</u> Klarnas betalningsmetod är aktiverad.

<u>Steg som ska återskapas:</u>

1. Gå till Commerce Admin **Lager** > **Konfiguration** > **Försäljning** > **Betalningsmetoder** > **Klarna** > **Klarna On-Site Messaging**.
1. Ange **Aktivera** till *Ja*.
1. Lämna **Designtema** fältet är tomt.
1. Spara konfigurationen genom att klicka på **Spara konfiguration**.
1. Gå till butiken och navigera till valfri produktsida.

<u>Förväntat resultat:</u>

Sidan läses in med standarddesigntemat för Klarna på plats-meddelanden.

<u>Faktiskt resultat:</u>

En tom sida visas.

## Lösning

Om du aktiverar klarna på plats-meddelanden ska du alltid se till att **Designtema** fältet är inte tomt.
