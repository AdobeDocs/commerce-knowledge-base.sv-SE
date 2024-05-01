---
title: Rapporten för verktyget för säkerhetsgenomsökning är tom
description: I den här artikeln finns en korrigering av problemet där verktyget för säkerhetsgenomsökning visar en tom sida i stället för den faktiska rapporten. För att lösa problemet kan du behöva lägga till de IP-adresser som används av verktyget till Tillåtelselista i brandväggen.
exl-id: e5f7f8c6-2dd3-44e3-8d19-f1f38d06dd6c
feature: Compliance, Security
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Rapporten för verktyget för säkerhetsgenomsökning är tom

I den här artikeln finns en korrigering av problemet där verktyget för säkerhetsgenomsökning visar en tom sida i stället för den faktiska rapporten. För att lösa problemet kan du behöva lägga till de IP-adresser som används av verktyget till Tillåtelselista i brandväggen.

## Berörda produkter och versioner:

* Adobe Commerce (alla distributionsmetoder) och Magento Open Source, Alla versioner

## Problem

<u>Steg som ska återskapas</u>:

1. Konfigurera säkerhetssökningsverktyget för att kontrollera din webbplats, enligt beskrivningen i [Säkerhetsgenomsökning](https://docs.magento.com/m2/ee/user_guide/magento/security-scan.html) i vår användarhandbok.
1. I åtgärdskolumnen väljer du **Kör genomsökning**.

<u>Förväntade resultat</u>:

Visa meddelande om rapportslutförande och möjlighet att öppna rapporten.

<u>Faktiska resultat</u>:

Inget meddelande och ingen rapport är tillgänglig.

## Orsak

Det här problemet kan uppstå eftersom verktyget för säkerhetsgenomsökning inte kunde nå din webbplats. Det innebär att webbplatsen inte kan nås alls eller att säkerhetssökningsverktyget blockeras.

## Lösning

Försök att öppna din webbplats.

* Om sidan läses in som den ska kan du behöva lägga till de IP-adresser som används av verktyget för säkerhetsgenomsökning i Tillåtelselista i brandväggen. Följande IP-adresser används: 52.87.98.44, 34.196.167.176, 3.218.25.102 vid portarna 80 och 443.
* Om webbplatsen inte läses in och returnerar *&quot;Det uppstod ett fel när din begäran bearbetades&quot;* kan du söka efter eventuella fel på webbplatsen.

## Relaterad läsning

* [Publicera och starta](https://devdocs.magento.com/guides/v2.3/cloud/live/live.html?_ga=2.73579601.273749082.1559572284-888339099.1547722854#security-scan) i vår dokumentation för utvecklare.
* [Säkerhetsgenomsökning](https://docs.magento.com/m2/ee/user_guide/magento/security-scan.html) i vår användarhandbok.
