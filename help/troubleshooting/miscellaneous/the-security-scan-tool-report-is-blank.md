---
title: Rapporten för verktyget för säkerhetsgenomsökning är tom
description: I den här artikeln finns en korrigering av problemet där verktyget för säkerhetsgenomsökning visar en tom sida i stället för den faktiska rapporten. För att lösa problemet kan du behöva lägga till de IP-adresser som används av verktyget till Tillåtelselista i brandväggen.
exl-id: e5f7f8c6-2dd3-44e3-8d19-f1f38d06dd6c
feature: Compliance, Security
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

1. Konfigurera verktyget för säkerhetsgenomsökning för att kontrollera din webbplats, enligt beskrivningen i [Säkerhetsgenomsökning](https://experienceleague.adobe.com/sv/docs/commerce-admin/systems/security/security-scan) i användarhandboken.
1. Välj **Kör skanning** i åtgärdskolumnen.

<u>Förväntade resultat</u>:

Visa meddelande om rapportslutförande och möjlighet att öppna rapporten.

<u>Faktiska resultat</u>:

Inget meddelande och ingen rapport är tillgänglig.

## Orsak

Det här problemet kan uppstå eftersom verktyget för säkerhetsgenomsökning inte kunde nå din webbplats. Det innebär att webbplatsen inte kan nås alls eller att säkerhetssökningsverktyget blockeras.

## Lösning

Försök att öppna din webbplats.

* Om sidan läses in som den ska kan du behöva lägga till de IP-adresser som används av verktyget för säkerhetsgenomsökning i Tillåtelselista i brandväggen. Följande IP-adresser används: 52.87.98.44, 34.196.167.176, 3.218.25.102 vid portarna 80 och 443.
* Om webbplatsen inte läses in och returnerar meddelandet *&quot;Det uppstod ett fel när din begäran skulle bearbetas&quot;* kontrollerar du om det finns eventuella fel på webbplatsen.

## Relaterad läsning

* [Publicera och starta](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/launch/overview) i utvecklardokumentationen.
* [Säkerhetsgenomsökning](https://experienceleague.adobe.com/sv/docs/commerce-admin/systems/security/security-scan) i vår användarhandbok.
