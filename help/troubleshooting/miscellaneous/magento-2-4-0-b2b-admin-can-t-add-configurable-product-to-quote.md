---
title: Adobe Commerce 2.4.0 B2B Admin kan inte lägga till en konfigurerbar produkt att citera
description: I den här artikeln beskrivs ett känt fel i Commerce Admin vid hantering av en B2B-offert. Det går inte att lägga till en konfigurerbar produkt med **SKU** i offerten. När du klickar på knappen **Lägg till i offert** fastnar redigeringssidan för **Quote**, och du kan inte konfigurera produkten och spara ändringar. Problemet uppstår också i Admin när en produkt läggs till av **SKU** i en beställning, eller när en produkt läggs till av **SKU** i **Avancerad utcheckning** (**Admin** &gt; **Kunder** &gt; **Alla kunder** &gt; **Hantera kundvagn**). Problemet åtgärdas i en patch för Adobe Commerce 2.4.1.
exl-id: 73f7231b-b496-4250-b9e2-29427c772d56
feature: Admin Workspace, B2B, Catalog Management, Configuration, Products, Quotes
role: Developer
source-git-commit: 05297c82b292b8ccc88018c58e991bd3a32d6ffa
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 B2B Admin kan inte lägga till en konfigurerbar produkt att citera

I den här artikeln beskrivs ett känt fel i Commerce Admin vid hantering av en B2B-offert. Det går inte att lägga till en konfigurerbar produkt av **SKU** i offerten. När du klickar på knappen **Lägg till i offert** låses redigeringssidan för **offert** in och du kan inte konfigurera produkten och spara ändringarna. Det här problemet inträffar även i Admin när **SKU** lägger till en produkt i en beställning, eller när en produkt läggs till av **SKU** i **Avancerad utcheckning** (**Admin** > **Kunder** > **Alla kunder** > **Kundredigering** > **Hantera SVE kundvagn**). Problemet åtgärdas i en patch för Adobe Commerce 2.4.1.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.4.0
* Adobe Commerce om molninfrastruktur 2.4.0

## Problem

<u>Förhandsvillkor</u>

* Adobe Commerce 2.4.0 är installerat.
* B2B är installerat.
* Ange att B2B-funktioner ska vara **Aktivera företag =** *Ja* , **Aktivera delad katalog =** *Nej* och **Aktivera B2B-offert =** *Ja*.
* Skapa ett kundkonto.
* Skapa ett företagskonto med den tidigare skapade kunden som företagsadministratör.
* Skapa en enkel produkt (Exempel: name &amp; **SKU** = TEST SIMPLE 1) som inte har tilldelats **Standard (Allmänt)**.
* Låt företagets administratör begära en offert med den enkla produkt som skapas ovan (Exempel: TEST SIMPLE 1).

<u>Steg som ska återskapas</u>

1. Gå till Commerce Admin-panelen.
1. Gå till **Försäljning > Offerter**.
1. Öppna **offerten**.
1. Klicka på knappen **Lägg till produkt efter SKU**.
1. Ange **SKU** för en annan (Exempel: TEST SIMPLE 2) produkt i **Ange SKU**-indatafältet.
1. Ange en giltig kvantitet i indatafältet **Antal**.
1. Klicka på knappen **Lägg till i offert**.

<u>Förväntade resultat</u>

* **Produkter som inte lagts till i rastret**, som innehåller namnet och **SKU** för den skapade produkten, visas som förväntat.
* När produkten har konfigurerats kan administratören lägga till den i **offerten** genom att klicka på knappen **Lägg till produkter i offert**, som förväntat.

<u>Faktiska resultat</u>

* **Produkter som inte lagts till i rastret**, som innehåller namnet och **SKU** för den skapade produkten, visas inte.
* Sidan **Citat** har fastnat vid inläsning.

## Rekommendation

För närvarande finns det ingen lösning på problemet med B2B-offertredigering, men för beställnings- och kundvagnshantering går det att välja produkter i **produktlistan** i stället för att lägga till dem med **SKU**. Det kommer att finnas en patch för att lösa problemet för Adobe Commerce 2.4.1, som kommer att släppas 4:e kvartalet 2020.

