---
title: Utcheckningssidor som inte läses in när annonsblockering är aktiverat
description: I den här artikeln finns en patch för det kända problemet med Adobe Commerce i molninfrastruktur 2.2.2 som gäller misslyckad inläsning av utcheckningssidor som orsakats av uBlock eller andra annonshämmare.
exl-id: fe718f21-df23-4ab1-a6b0-03bad4d7095d
feature: Checkout, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# Utcheckningssidor som inte läses in när annonsblockering är aktiverat

I den här artikeln finns en patch för det kända problemet med Adobe Commerce i molninfrastruktur 2.2.2 som gäller misslyckad inläsning av utcheckningssidor som orsakats av uBlock eller andra annonshämmare.

## Problem

Om Google Analytics är aktiverat för butiken blockeras filen `trackingCode.js` från att läsas in och RequireJS bryter JS-körningsflödet när en kund med installerat uBlock eller annan annonsblockerare går vidare till kassan. Detta orsakar problem vid inläsning av utcheckningssidan.

<u>Steg som ska återskapas</u> :

Krav: En annonsblockerare måste vara installerad och aktiv i webbläsaren.

1. Aktivera och konfigurera Google Analytics-funktionen i Commerce Admin.
1. Öppna en produktsida i butiken.
1. Lägg produkter i kundvagnen.
1. Klicka på länken **Gå till kassan**.

<u>Förväntat resultat</u>: Utcheckningssidan läses in och kunden kan slutföra utcheckningen.

<u>Faktiskt resultat</u>: Utcheckningssidan läses inte in. Inläsningsrotationen försvinner aldrig.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[Hämta MDVA-9353\_EE\_2.2.2\_v1.composer.patch](assets/MDVA-9353_EE_2.2.2_v1.composer.patch.zip)

### Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce om molninfrastruktur 2.2.2

Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce i molninfrastruktur från 2.1.0 till 2.1.14
* Adobe Commerce i molninfrastruktur från 2.2.0 till 2.2.1 och 2.2.3 till 2.2.5
* Adobe Commerce lokalkontor mellan 2.1.0 och 2.1.14
* Adobe Commerce lokalt från 2.2.0 till 2.2.5

## Så här sätter du på plåstret

Instruktioner finns i [Använda en dispositionsruta från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.

## Användbara länkar

* [Problemet diskuterades på GitHub](https://github.com/magento/magento2/pull/13061)

## Bifogade filer
