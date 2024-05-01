---
title: Fel datum för specialpris
description: I den här artikeln finns en korrigeringsfil för det kända Adobe Commerce 2.2.2-problemet som gäller att produktens"from"-datum är felaktigt om dess värde ändras av administratören vars gränssnittsspråk är annorlunda.
exl-id: fc109550-951e-4900-97e3-4ff3e7e5a395
feature: Orders, Personalization, User Account
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Fel datum för specialpris

I den här artikeln finns en korrigeringsfil för det kända Adobe Commerce 2.2.2-problemet som gäller att produktens&quot;from&quot;-datum är felaktigt om dess värde ändras av administratören vars gränssnittsspråk är annorlunda.

## Problem

När du anger/ändrar specialpriset för en produkt sparas aktuellt datum och tid i databasen som ett värde för `special_from_date` -attribut (inte synligt när du redigerar en produkt). Om du redigerar specialpriset och ditt administratörsanvändarkonto är inställt på ett annat språkområde för gränssnittet kan ett felaktigt värde anges till `special_from_date` på grund av problem med att analysera datumformat för olika språkområden.

<u>Steg som ska återskapas</u>:

Krav: administratörens nationella inställningar är engelska (USA).

1. Logga in på Commerce Admin.
1. Gå till inställningarna för administratörens användarkonto.
1. Ange gränssnittets språkområde som ukrainskt.
1. Klicka **Spara konto**.
1. Gå till **Katalog** > **Produkt**.
1. Välj valfri produkt.
1. Klicka på **Avancerade priser**.
1. Lägg till ett specialpris.
1. Spara produkten.
1. Upprepa steg 7-9.
1. Gå till **System** > **Åtgärdsloggar**.
1. Sök efter produktuppdateringar i loggen.

<u>Förväntade resultat</u>:

Startdatumet för specialpriset ska vara det aktuella datumet.

<u>Faktiska resultat</u>:

Startdatumet för specialpriset är ett datum som infaller några år i framtiden och förhindrar att specialpriset är aktivt.

## Lösning

Om du tillämpar korrigeringen kan du inte få problemet att hända igen. Om du vill korrigera data för de produkter där datumet var felaktigt inställt sätter du om specialpriset efter att du tillämpat korrigeringen.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[Hämta MDVA-11605\_EE\_2.2.2\_COMPOSER\_v1.patch](assets/MDVA-11605_EE_2.2.2_COMPOSER_v1.patch.zip)

### Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce (alla distributionsmetoder) 2.2.2

Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce lokal 2.1.0-2.1.18, 2.2.0-2.2.5
* Adobe Commerce om molninfrastruktur 2.1.11-2.1.18, 2.2.0-2.2.5

## Så här sätter du på plåstret

Se [Använda en kompositkorrigering från Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) för instruktioner.

## Bifogade filer
