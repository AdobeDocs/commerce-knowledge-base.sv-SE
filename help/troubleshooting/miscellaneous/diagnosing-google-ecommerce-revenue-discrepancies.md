---
title: Diagnostisera intäktsavvikelser i Google eCommerce
description: '"Den här artikeln innehåller lösningar för skillnader mellan Google och Magento Business Intelligence (MBI). Google eCommerce tracking ger både ditt Google Analytics-konto och dina MBI-instrumentpaneler kraft, men det leder till att många kunder frågar oss: Bör båda verktygen rapportera samma mängd **order** och **intäkt**?'''
exl-id: b2e43e70-d234-4338-ae81-fa401416be5a
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 0%

---

# Diagnostisera intäktsavvikelser i Google eCommerce

I den här artikeln beskrivs lösningar för skillnader mellan Google och Magento Business Intelligence (MBI). Google eCommerce tracking ger både ditt Google Analytics-konto och dina MBI-instrumentpaneler kraft, men det leder till att många kunder frågar oss: Ska båda verktygen rapportera samma belopp för **order** och **intäkter**?

Enligt vår erfarenhet är svaret&quot;nej&quot; i nästan alla fall. Detta beror på att Google eCommerce tracking hämtar orderinformationen under en knappklickningshändelse på din webbplats, som saknar många orderattribut som registreras senare i tiden i din databas - allt från order som inte registreras till att senare annulleras eller återbetalas.

Vi vet att diskrepanser mellan Google och MBI kan skapa osäkerhet för dig och ditt team. Vi vill hjälpa dig att förstå skillnaden mellan dessa två tal, vilket kan medföra att du kan justera ditt Google-konto eller din databas.

## Varför rapporterar GA **mindre** intäkter än min databas?

När Google Analytics underrapporterar order och intäkter är det en indikation på att det inte fångar upp alla order som görs på er webbplats. Eftersom du vet att dina databasdata är det definitiva numret kan du vidta några åtgärder för att fastställa grundorsaken och eventuellt hjälpa Google att samla in mer information.

* Du har inte alltid aktiverat spårning för e-handel i Google. Försök att titta på en mindre, nyare period.
* Din spårning för Google eCommerce är inte konfigurerad för att hämta köp från vissa webbläsare, operativsystem eller enheter.
* Klickhändelsen som är kopplad till din Google eCommerce-spårning spårar inte korrekt moms, frakt eller andra avgifter utöver ordersumman.
* Databasens tidsstämpel är i en annan tidszon än Google Analytics tidsstämpel.
* Folk kan besöka din webbplats via inkognitiva fönster eller med cookies inaktiverade.

## Varför rapporterar GA **fler** intäkter än min databas?

Vi har funnit att det är vanligare för Google Analytics att överrapportera order och intäkter jämfört med en e-handelsdatabas. Det här är inte alltid dåligt. Din databas är det slutgiltiga antalet transaktioner som har gjorts på din webbplats, och det finns flera skäl till att Google kan rapportera mycket även om du har konfigurerat den perfekt:

* eCommerce tracking samlar in duplicerade knappklickningar som bara registreras som en enda order i databasen.
* Du har ett stort antal annullerade, återfinansierade eller bedrägliga order, vilket är en statusändring som inträffar när eCommerce spårar data.
* Måtten **Inkomster** och **Beställningar** utesluter avsiktligt test- eller interna order, som inte kan differentieras i Google.
* Det går inte att placera beställningar i databasen under vissa omständigheter.
* Google eCommerce tracking känner inte till kuponger och rabatter på ordern.
* Databasens tidsstämpel är i en annan tidszon än Google Analytics tidsstämpel.

Tänk på att även om Google rapporterar ett högre antal än din databas saknas det troligen några beställningar av de orsaker som anges i avsnittet ovan.

## Felsökning

* Skapa en klon av dina **intäktsmått**-mått utan filter som begränsar resultatet. Filtren för beställningar vi räknar eller kunder vi räknar är viktiga, men Google har inget motsvarande filter.
* Granska en liten nyligen gjord period, till exempel ett intervall på några timmar tidigare den här veckan.
* När du har konfigurerat Google e-handelsspårning i MBI kan du använda Filter eller Gruppera efter för att granska en enskild Source, Medium eller Campaign. Gör sedan samma sak i Google. En källa med mindre trafik/intäkter blir bättre, eftersom den har mindre felmarginal.
