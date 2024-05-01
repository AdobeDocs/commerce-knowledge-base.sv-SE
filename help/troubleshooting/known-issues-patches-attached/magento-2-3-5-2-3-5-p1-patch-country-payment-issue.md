---
title: "Adobe Commerce 2.3.5, 2.3.5-p1 patch: landbetalningsproblem"
description: Den här korrigeringen åtgärdar ett problem i Adobe Commerce där arbetsflödet för utcheckning i butiken inte visade någon betalningsmetod som har aktiverats för specifika länder, med undantag för Klarna och Amazon Pay.
exl-id: e205e35e-9ffe-4826-b951-3a3caf1e0621
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Adobe Commerce 2.3.5, 2.3.5-p1 patch: landbetalningsproblem

Den här korrigeringen åtgärdar ett problem i Adobe Commerce där arbetsflödet för utcheckning i butiken inte visade någon betalningsmetod som har aktiverats för specifika länder, med undantag för Klarna och Amazon Pay.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.3.5 och 2.3.5-p1
* Adobe Commerce lokal 2.3.5 och 2.3.5-p1

## Problem

När en butik har Amazon Pay och en annan betalning har tilldelats till olika länder, och när något av dessa länder och betalningsmetoder har valts, visas inte knapparna för betalningsmetod och placering av order.

En uppdatering av en webbsida är en tillfällig lösning på problemet.

För att lösa problemet och ta bort felet har vi skapat ett [patch](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip).

<u>Förutsättningar</u>:

* En enkel produkt skapas.
* **Check-/penningorder** aktiveras endast för specifika länder (på **Butik** > **Konfiguration** > **Försäljning** > **Betalningsmetoder**).

* Exempel: Betalning från tillämpliga länder = särskilda länder
* Exempel: Betalning från specifika länder = Storbritannien

<u>Steg som ska återskapas</u>:

1. Gå till Storefront som gäst.
1. Lägg en enkel produkt i kundvagnen.
1. Gå till kassan.
1. Fyll i formuläret med giltiga data.

   * Land = *Amerikas förenta stater*

1. Välj fraktkostnad och klicka **Nästa**.

   * Betalningssteget öppnas.
   * Det finns inga tillgängliga betalningar.
   * Meddelande: **Det finns ingen betalningsmetod tillgänglig.**
   * Det finns inga **Montera beställning** -knappen.

1. Gå tillbaka till **Leveranssteg** och ändra värdet till:

   * Land = *Förenade kungariket*

1. Välj fraktkostnad och klicka **Nästa**.

<u>Förväntat resultat</u>:

Betalningssteget öppnas.

* **Kontant vid leverans** visas.
* **Check-/penningorder** visas.
* The **Montera beställning** visas.

<u>Faktiskt resultat</u>:

Betalningssteget öppnas.

* Det finns inga tillgängliga betalningar.
* Meddelande: *Det finns ingen betalningsmetod tillgänglig.*
* Det finns inga **Montera beställning** -knappen.

## Lösning

[Tillämpa korrigeringen](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip) nedan.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[Ladda ned BUNDLE-2546\_EE\_2.3.5-p1.comser.patch](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip)

### Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce om molninfrastruktur 2.3.5 och 2.3.5-p1
* Adobe Commerce lokal 2.3.5 och 2.3.5-p1

Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce version 2.3.4-p2 - 2.2.6

## Så här sätter du på plåstret

Se [Använda en kompositkorrigering från Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support för instruktioner.

## Bifogade filer
