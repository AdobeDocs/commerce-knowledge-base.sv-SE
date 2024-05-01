---
title: Adobe Commerce 2.4.0 B2B Admin kan inte lägga till en konfigurerbar produkt att citera
description: I den här artikeln beskrivs ett känt fel i Commerce Admin vid hantering av en B2B-offert. Det går inte att lägga till en konfigurerbar produkt med **SKU** i offerten. När du klickar på knappen **Lägg till i offert** fastnar redigeringssidan för **Quote**, och du kan inte konfigurera produkten och spara ändringar. Problemet uppstår också i Admin när en produkt läggs till av **SKU** i en beställning, eller när en produkt läggs till av **SKU** i **Avancerad utcheckning** (**Admin** &gt; **Kunder** &gt; **Alla kunder** &gt; **Kundredigering***; **Hantera kundvagn*). Problemet åtgärdas i en patch för Adobe Commerce 2.4.1.
exl-id: 73f7231b-b496-4250-b9e2-29427c772d56
feature: Admin Workspace, B2B, Catalog Management, Configuration, Products, Quotes
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 B2B Admin kan inte lägga till en konfigurerbar produkt att citera

I den här artikeln beskrivs ett känt fel i Commerce Admin vid hantering av en B2B-offert. Det går inte att lägga till en konfigurerbar produkt per **SKU** till offerten. När du klickar **Lägg till i offert** -knappen **Citat** sidan för redigering har fastnat och du kan inte konfigurera produkten och spara ändringarna. Problemet inträffar även i Admin när en produkt läggs till av **SKU** till en order eller lägga till en produkt efter **SKU** in **Avancerad utcheckning** (**Administratör** > **Kunder** > **Alla kunder** > **Kundredigering** > **Hantera kundvagn**). Problemet åtgärdas i en patch för Adobe Commerce 2.4.1.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.4.0
* Adobe Commerce om molninfrastruktur 2.4.0

## Problem

<u>Förhandsvillkor</u>

* Adobe Commerce 2.4.0 är installerat.
* B2B är installerat.
* Ange att B2B-funktioner ska **Aktivera företag =**  *Ja* , **Aktivera delad katalog =**  *Nej* och **Aktivera B2B-citat =**  *Ja*.
* Skapa ett kundkonto.
* Skapa ett företagskonto med den tidigare skapade kunden som företagsadministratör.
* Skapa en enkel produkt (Exempel: namn &amp; **SKU** = TEST SIMPLE 1) som inte har tilldelats **Standard (Allmänt)**.
* Låt företagets administratör begära en offert med den enkla produkt som skapas ovan (Exempel: TEST SIMPLE 1).

<u>Steg som ska återskapas</u>

1. Gå till Commerce Admin-panelen.
1. Gå till **Försäljning > Offerter**.
1. Öppna **Citat**.
1. Klicka på **Lägg till produkt efter SKU** -knappen.
1. Ange **SKU** av en annan (Exempel: TEST SIMPLE 2) produkt i **Ange SKU** indatafält.
1. Ange en giltig kvantitet i **Antal** indatafält.
1. Klicka på **Lägg till i offert** -knappen.

<u>Förväntade resultat</u>

* The **Produkter som inte lagts till i offerten** rutnät, som innehåller namnet och **SKU** av den skapade produkten visas som förväntat.
* När produkten har konfigurerats kan administratören lägga till den i **Citat** genom att klicka på **Lägg till produkter i offert** som förväntat.

<u>Faktiska resultat</u>

* The **Produkter som inte lagts till i offerten** rutnät, som innehåller namnet och **SKU** för den skapade produkten visas inte.
* The **Citat** sidan har fastnat vid inläsning.

## Rekommendation

För närvarande finns det ingen lösning på problemet med B2B-offertredigering, men för beställnings- och kundvagnshantering är det möjligt att välja produkter från **Produktlista** i stället för att lägga till dem med **SKU**. Det kommer att finnas en patch för att lösa problemet för Adobe Commerce 2.4.1, som kommer att släppas 4:e kvartalet 2020.

## Relaterad läsning

* [Problem med Adobe Commerce 2.4.0: Uppdatering av kundens aktiviteter fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 Known Issue: Raw message data display on Storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 Känt fel: Exportskattesatser fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 Känt fel: Visningsfel för beställningar](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
