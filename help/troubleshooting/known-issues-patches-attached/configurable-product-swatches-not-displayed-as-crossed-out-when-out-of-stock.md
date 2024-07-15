---
title: Konfigurerbara färgrutor visas inte överstruken när de inte finns i lager
description: I den här artikeln finns en patch för det kända Adobe Commerce 2.2.2-problemet som gäller att de konfigurerbara färgrutorna ligger utanför lagret och inte visas som de är på framsidan.
exl-id: 79c59a3f-a94b-4726-8af1-5fe754ea95a5
feature: Configuration, Orders, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Konfigurerbara färgrutor visas inte överstruken när de inte finns i lager

I den här artikeln finns en patch för det kända Adobe Commerce 2.2.2-problemet som gäller att de konfigurerbara färgrutorna ligger utanför lagret och inte visas som de är på framsidan.

## Problem

När du har en konfigurerbar produkt, och för en viss kombination av alternativ, är den relaterade enkla produkten inte i lager, är färgrutan fortfarande tillgänglig och kan väljas i butiken.

<u>Steg som ska återskapas</u>:

1. I Commerce Admin skapar du en konfigurerbar produkt med alternativ för två attribut: color (red, black) och size (S, M, L).
1. Ange Kvantitet som &quot;1&quot; för varje motsvarande enkel produkt.
1. Lägg till rött, M-produkt i kundvagnen och kassan i butiken.
1. Bearbeta ordern i Admin så att artikelkvantiteten uppdateras till &quot;0&quot;.
1. Se till att restorder inte tillåts.
1. Navigera till samma produktsida i butiken och välj samma alternativ: röd, M.

<u>Förväntade resultat</u>:

Den röda färgrutan M har ett rött snedstreck och kan inte markeras.

<u>Faktiska resultat</u>:

Den röda färgrutan M kan markeras.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[Ladda ned MDVA-8215\_EE\_2.2.2\_v1.comser.patch](assets/MDVA-8215_EE_2.2.2_v1.composer.patch.zip)

### Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce (alla distributionsmetoder) 2.2.2

Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce lokalt och Adobe Commerce om molninfrastruktur 2.2.0-2.2.3

## Så här sätter du på plåstret

Mer information finns i [Använda en dispositionsruta från Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## Bifogade filer
