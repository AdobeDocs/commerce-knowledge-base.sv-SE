---
title: '""500-fel" efter att ha dubbelklickat på länken Ta bort i kundvagnen"'
description: I den här artikeln finns en patch till det kända problemet med Adobe Commerce i molninfrastruktur 2.2.0 som handlar om att kunderna får felmeddelanden när de försöker ta bort en varukorg två gånger (genom att dubbelklicka på länken *Ta bort* eller genom att klicka på den på olika flikar).
exl-id: 927cf681-febf-42cc-8db5-469bcf8f2012
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# &quot;500-fel&quot; efter att ha dubbelklickat på länken Ta bort i kundvagnen

I den här artikeln finns en patch för det kända problemet med Adobe Commerce i molninfrastruktur 2.2.0 som handlar om att kunder får felmeddelanden när de försöker ta bort två gånger en kundvagnsartikel (genom att dubbelklicka på länken *Ta bort* eller genom att klicka på den på olika flikar).

## Problem

När kunderna dubbelklickar på länken *Ta bort* i kundvagnen och försöker ta bort en produkt från kundvagnen visas en tom sida med följande felmeddelande: *&quot;Den här sidan fungerar inte. HTTP-FEL 500&quot;.* Samma problem uppstår om en kund öppnar två webbläsarflikar med kundvagnssidan och tar bort produkten först på en flik, sedan på den andra.

<u>Steg som ska återskapas</u> :

1. Lägg en produkt i kundvagnen i butiken.
1. Navigera till kundvagnssidan.
1. Dubbelklicka på länken Ta bort.

ELLER

1. Lägg en produkt i kundvagnen i butiken.
1. Navigera till kundvagnssidan.
1. Öppna en ny flik i webbläsaren och gå till kundvagnssidan (samma produkt).
1. Ta bort produkten från vagnen.
1. Öppna den andra fliken och ta bort produkten igen.

<u>Förväntat resultat</u> : Produkten tas bort från vagnen utan fel.

<u>Faktiskt resultat</u> : Produkten tas bort med felet: *&quot;Den här sidan fungerar inte. HTTP ERROR 500*-felmeddelande.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[Hämta MDVA-8623\_EE\_2.2.0\_v1.composer.patch](assets/MDVA-8623_EE_2.2.0_v1.composer.patch.zip)

## Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce om molninfrastruktur 2.2.0

Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce om molninfrastruktur 2.2.1 - 2.2.5
* Adobe Commerce lokal 2.2.0 - 2.2.5

## Så här sätter du på plåstret

Instruktioner finns i [Använda en dispositionsruta från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.

## Bifogade filer
