---
title: "Adobe Commerce 2.4.0 known issue: order display error"
description: "Den här artikeln innehåller en lösning på ett känt problem i Adobe Commerce för ett ordervisningsfel. När inloggade kunder granskar sina beställningar på menyn **Mitt konto** (**Mitt konto&gt; Mina beställningar**) kan inte orderrastret ändra antalet beställningar per sida till 20 från sidan 2 när det finns 11 beställningar. Om det finns fler beställningar än vad som är konfigurerat att visas per sida visas felmeddelandet när du navigerar till den sista sidan med beställningar och ändrar antalet beställningar per sida: *Du har inte gjort några beställningar*. Problemet kommer att lösas i Adobe Commerce 2.4.1."
exl-id: a6d300e1-1cbc-42b9-997d-d72f8765517b
feature: B2B, Categories, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: fel vid visning av beställningar

I den här artikeln finns en lösning på ett känt problem i Adobe Commerce för ett ordervisningsfel. När inloggade kunder granskar sina order i **Mitt konto** meny (**Mitt konto > Mina beställningar**) går det inte att ändra antalet order per sida till 20 från sida 2 när det finns 11 order. Om det finns fler order än vad som är konfigurerat att visas per sida visas felmeddelandet när du navigerar till den sista sidan med order: *Du har inte gjort några beställningar*. Problemet kommer att lösas i Adobe Commerce 2.4.1.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.4.0
* Adobe Commerce om molninfrastruktur 2.4.0

## Problem

<u>Förutsättningar</u>

* Adobe Commerce 2.4.0 är installerat.
* Skapa minst en kategori och en enkel produkt.

<u>Steg som ska återskapas</u>

1. Skapa 11 order med produkter.
1. Gå till **Mitt konto**.
1. Gå till **Mina beställningar**.
1. Klicka på den andra sidan om du vill visa den elfte ordningen i orderrastret.
1. Välj **Visa = 20 per sida** i listrutan.

<u>Förväntat resultat</u>

Alla 11 order visas som förväntat på den första sidan.

<u>Faktiskt resultat</u>

The *Du har inte gjort några beställningar* felmeddelande visas.

## Tillfällig lösning

Den tillfälliga lösningen är att få köparen att öppna igen **Mina beställningar** och sedan visas orderlistan korrekt. Problemet kommer att åtgärdas i nästa version, Adobe Commerce 2.4.1, som kommer att släppas 4:e kvartalet 2020.

## Relaterade läsningar i vår kunskapsbas

* [Problem med Adobe Commerce 2.4.0 - uppdateringen av kundens aktiviteter fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 Known Issue: Raw message data display on Storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 Känt fel: Exportskattesatser fungerar inte](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B Admin kan inte lägga till en konfigurerbar produkt att citera](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
