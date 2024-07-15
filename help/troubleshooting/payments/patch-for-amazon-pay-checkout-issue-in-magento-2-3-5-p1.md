---
title: Patch for Amazon Pay checkout issue in Adobe Commerce 2.3.5-p1
description: Den här korrigeringen åtgärdar problemet med att det inte går att ändra en betalningsmetod vid utcheckning av steget "Granska och betalningar" från betalningswidgeten när du checkar ut med Amazon Pay in Adobe Commerce.
exl-id: a241f67f-019c-4ff2-a5ad-e7dc71639768
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Patch for Amazon Pay checkout issue in Adobe Commerce 2.3.5-p1

Den här korrigeringen åtgärdar problemet med att det inte går att ändra en betalningsmetod vid utcheckning av steget &quot;Granska och betalningar&quot; från betalningswidgeten när du checkar ut med Amazon Pay in Adobe Commerce.

## Berörda produkter och versioner

* Adobe Commerce on cloud infrastructure version 2.3.5-p1
* Adobe Commerce lokal version 2.3.5-p1

## Problem

När en kund checkar ut med Amazon Pay, loggar in, fortsätter till betalningssteget och försöker ändra sitt betalkort från betalningswidgeten visas ett felmeddelande. Utcheckningen kan inte slutföras om kunden ignorerar felet och fortsätter till utcheckningen.

För att lösa problemet och ta bort felet har vi skapat en [patch](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip).

<u>Steg som ska återskapas</u>:

1. Starta kassan med Amazon Pay.
1. Logga in som Amazon Pay-kund.
1. Välj leveranssätt och fortsätt till betalningssteget.
1. Försök att byta kreditkort till ett annat.

<u>Förväntat resultat</u>: Ett annat kreditkort har valts som betalningsmetod utan fel.

<u>Faktiskt resultat</u>: Felmeddelandet visas: *&quot;Kontakta återförsäljaren för att få hjälp med att slutföra din beställning.&quot;*

## Lösning

[Använd korrigeringen](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip) nedan.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[Ladda ned BUNDLE-2554\_EE\_2.3.5-p1.comser.patch](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip)

### Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce on cloud infrastructure version 2.3.5-p1
* Adobe Commerce lokal version 2.3.5-p1

Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce on cloud infrastructure version 2.3.5
* Adobe Commerce lokal version 2.3.5

## Så här sätter du på plåstret

Mer information finns i [Använda en dispositionsruta från Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.

## Bifogade filer
