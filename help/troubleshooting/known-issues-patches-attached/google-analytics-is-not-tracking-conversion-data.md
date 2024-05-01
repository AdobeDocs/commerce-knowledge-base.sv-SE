---
title: Google Analytics spårar inte konverteringsdata
description: I den här artikeln finns en patch för det kända Adobe Commerce 2.2.4-problemet som rör Google Analytics som inte spårar konverteringsdata.
exl-id: b9012fd1-4f90-41e9-9559-0343ee052ec6
feature: Configuration, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Google Analytics spårar inte konverteringsdata

I den här artikeln finns en patch för det kända Adobe Commerce 2.2.4-problemet som rör Google Analytics som inte spårar konverteringsdata.

>[!NOTE]
>
>Problemet har åtgärdats i Adobe Commerce 2.2.6.

## Problem

Konverteringsdata spårades inte av Google Analytics på grund av ett fel i Google Analytics-komponentkoden.

<u>Steg som ska återskapas</u>:

1. Aktivera och konfigurera funktionaliteten Google Analytics i Commerce Admin under **Lager** > **Inställningar** > **Konfiguration** > **Försäljning** > **GOOGLE API** > **Google Analytics**.
1. Klicka **Spara konfiguration**.
1. Lägg en order i butiken.
1. Gå till **Google Analytics Dashboard** > **Konverteringar** > **Ökning**.
1. Ange datumintervallet till aktuellt datum.

<u>Förväntat resultat</u>:

Ordningen visas i konverteringsdata.

<u>Faktiskt resultat</u>:

Ordningen visas inte i konverteringsdata.

## Lösning

Korrigeringen åtgärdar felet i Google Analytics-komponentkoden. När korrigeringskonverteringsdata har tillämpats spåras de av Google Analytics.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[Ladda ned MDVA-11263\_EE\_2.2.4\_v1.comser.patch](assets/MDVA-11263_EE_2.2.4_v1.composer.patch.zip)

### Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce lokal 2.2.4

Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce lokal 2.2.5
* Adobe Commerce om molninfrastruktur 2.2.4, 2.2.5

## Så här sätter du på plåstret

Se [Använda en kompositkorrigering från Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) för instruktioner.

## Bifogade filer
