---
title: Låga prestanda för webbplats och API
description: I den här artikeln finns en patch för det kända problemet med Adobe Commerce i molninfrastruktur 2.2.1 som rör låg prestanda för webbplatser och API som orsakats av en lång tid som krävs för att skriva "debug.log".
exl-id: b71816cd-f580-4c80-9694-585ed051a56d
feature: REST, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Låga prestanda för webbplats och API

I den här artikeln finns en patch för det kända problemet med Adobe Commerce i molninfrastruktur 2.2.1 som handlar om att ha låg plats och API-prestanda på grund av att man måste skriva mycket länge `debug.log`.

## Problem

Webbplatsens prestanda är långsam. API-åtgärder går långsamt, till exempel att uppdatera produkter med `PUT` -metod. När du tar en närmare titt på åtgärderna som använder New Relic förbrukas de flesta minnen och processorn av att skriva till `/var/log/debug.log`.

## Lösning

Lös problemet genom att applicera plåstret. Korrigeringen delar och skriver loggar, betalningsmetoder och leveransmetoder till separata filer.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[Hämta MDVA-8371\_EE\_2.2.1\_COMPOSER\_v2.patch](assets/MDVA-8371_EE_2.2.1_COMPOSER_v2.patch.zip)

### Kompatibla Adobe Commerce-versioner

Korrigeringen skapades för:

* Adobe Commerce i molninfrastruktur 2.2.1

Patchen är också kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe:

* Adobe Commerce om molninfrastruktur 2.2.0, 2.2.2, 2.2.3
* Adobe Commerce lokal 2.2.0, 2.2.2, 2.2.3

## Så här sätter du på plåstret

Se [Använda en kompositkorrigering från Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support för instruktioner.

## Bifogade filer
