---
title: "Problem med Adobe Commerce 2.4.1: det går inte att ändra Amazon-konto i Chrome"
description: I den här artikeln beskrivs ett känt Adobe Commerce 2.4.1-problem där kunder loggar in på tidigare använda Amazon-konton i stället för att föreslås logga in när de använder Amazon Pay vid utcheckning.
exl-id: 8acffe99-b3ec-4b45-9434-61b66e963838
feature: Customer Service
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 utgåva: det går inte att ändra Amazon-konto i Chrome

I den här artikeln beskrivs ett känt Adobe Commerce 2.4.1-problem där kunder loggar in på tidigare använda Amazon-konton i stället för att föreslås logga in när de använder Amazon Pay vid utcheckning.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.4.1
* Adobe Commerce i molninfrastruktur 2.4.1

## Problem

Kunder loggas in på tidigare använda Amazon-konton i stället för att föreslås logga in när de använder Amazon Pay vid utcheckning.

<u>Steg att återskapa:</u>

1. I butiken lägger du till en artikel i kundvagnen och fortsätter till gästutcheckningen.
1. Klicka på knappen **Amazon Pay** . Amazon.com för inloggning visas.
1. Logga in på Amazon-kontot.
1. Välj en adress och klicka på **Nästa**.
1. Välj betalningsmetod.
1. Klicka på **Montera order**.
1. Gå tillbaka till startsidan och logga in på butikskontot.
1. Lägg till en artikel i kundvagnen igen och fortsätt till kassan.
1. Klicka på knappen **Amazon Pay** .

<u>Faktiskt resultat:</u>

Du loggas automatiskt in på det tidigare använda (steg 3) Amazon-kontot igen.

<u>Förväntat resultat:</u>

Amazon.com för inloggning visas och du kan logga in eller skapa ett nytt konto för Amazon Pay.

## Orsak

Problemet kan inträffa i följande situationer:

* När cookie-värdet `SameSite` är `LAX` skickas inte cookien som en del av några tredjepartsanrop.
* Funktionen för blockering av innehåll i Mozilla Firefox förhindrar att tredje part spårar webbläsaranvändarnas aktiviteter genom att blockera användningen av skript och lagringsmekanismer på klientsidan. I Firefox används en extern leverantör, Disconnect.me, för att skapa en lista över spårningswebbplatser som ska blockeras. Amazon Pay använder en iframe på en tredjepartswebbplats för att returnera en åtkomsttoken efter inloggning och återge adress- och plånbokswidgeten. Med funktionen för blockering av innehåll betraktas inläsningsbegäranden för iframe-adresser från Amazon som externa spårningsbegäranden och blockeras, vilket gör att köparen inte kan fortsätta med utcheckningen.
* Om cookies eller JS från tredje part uttryckligen blockeras av webbläsaren.

## Lösning

Kontrollera att förfrågningar från Amazon Pay iframe inte blockeras av webbläsare.
