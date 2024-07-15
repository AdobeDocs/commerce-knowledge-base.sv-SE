---
title: Visa miljöns vCPU-nivå i ditt kluster på Adobe Commerce
promoted: true
description: I den här artikeln beskrivs hur du kontrollerar din nivåtilldelning för vCPU med hjälp av fliken New Relic Infra i Observation for Adobe Commerce. Observation for Adobe Commerce är en New Relic-nördlet som visar status för din Adobe Commerce-webbplats, aktuella vyer och vyer över tidigare tidsperioder.
exl-id: a0332e7e-d38d-47d3-b3da-293902f45edc
source-git-commit: 309fda5284de3b8be54e95bf2bfd8ff1777b6c90
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Visa miljöns vCPU-nivå i ditt kluster på Adobe Commerce

I den här artikeln beskrivs hur du kontrollerar din nivåtilldelning för vCPU med hjälp av fliken New Relic Infra i Observation for Adobe Commerce. Observation for Adobe Commerce är en New Relic-nördlet som visar status för din Adobe Commerce-webbplats, aktuella vyer och vyer över tidigare tidsperioder.

## Berörda produkter och versioner:

Adobe Commerce om molninfrastruktur 2.4.3 - 2.4.6

## Kontrollera allokering av vCPU-nivå med observationer för Adobe Commerce:

Så här kommer du åt och loggar in på New Relic Observation for Adobe Commerce ndlet:

1. Klicka på **Appar** på startsidan för New Relic.
1. Klicka på **Observation för Adobe Commerce**.
1. Observationen för Adobe Commerce nördlet öppnas.
1. Klicka på listrutan **Välj ett konto** och välj ett konto.
1. Du kan fylla i projekt-ID:t, New Relic-kontonumret eller kontonamnet eller bläddra igenom listan med konton.
1. Klicka på den ljusblå listrutemenyn med klockikonen (mot den övre högra delen av nördletsfönstret).
1. Om du försöker identifiera orsaken till en händelse/ett fel ska du välja en tid före biljettdatumet och -tiden för att se om det fanns några föregående händelser/data. Du kan använda de förinställda tidsbildrutorna eller ange en anpassad tidsbildruta genom att välja **Ange anpassad**.
1. Klicka på **Information** på flikarna. Det finns tre vCPU-skiktdiagram:
   * I det första diagrammet visas **vCPU-nivåvy över tidslinjen GREATER 2 veckor (du måste välja en tidslinje GREATER mer än 2 veckor). Obs! Samplingsfrekvensen kommer att vara per dag. Om kluster har upp- och nedstorlekar på en dag visas slutskiktsstorleken följande dag:**.
   * I det andra diagrammet visas **vCPU-nivåvy över tidslinjen (du måste välja en tidslinje som är större än 24 timmar men inte större än 2 veckor)**.
   * I det tredje diagrammet visas **vCPU-nivåvyn över tidslinjen BY NODE, som ska titta på tidslinjen mindre än 24 timmar**.

## Relaterad läsning

* [Observation för Adobe Commerce - översikt](/help/support-tools/observation-for-adobe-commerce/observation-adobe-commerce-overview.md) i vår kunskapsbas för support.
