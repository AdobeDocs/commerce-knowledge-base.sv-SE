---
title: Beställningar som inte visas i beställningsrutnätet i administratören
description: I den här artikeln finns en patch för det kända Adobe Commerce 2.2.1-problemet som gäller beställningar som inte visas i beställningsrutnätet i Commerce Admin.
exl-id: b8376760-6558-41ed-8c6b-51c5759e831a
feature: Admin Workspace, B2B, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# Beställningar som inte visas i beställningsrutnätet i administratören

I den här artikeln finns en patch för det kända Adobe Commerce 2.2.1-problemet som gäller beställningar som inte visas i beställningsrutnätet i Commerce Admin.

## Problem

I Adobe Commerce 2.2.1 med B2B-tillägg installerat visas inte order som skapats i butiken av en registrerad kund i listan över order på kundens konto i Commerce Admin. I felsökningsloggen (`./var/log/debug.log`) loggas följande fel:

`report.CRITICAL: You cannot define a correlation name ‘company_order’ more than once`

<u>Förutsättningar</u>:

Din butikskatalog innehåller produkter, inte Adobe Commerce exempeldata, och B2B-tillägget installeras.

<u>Steg som ska återskapas</u>:

1. Navigera till butiken och skapa ett kundkonto.
1. Lägg en produkt i kundvagnen, slutför utcheckningen och skicka en order.
1. Logga in på Admin.
1. Navigera till **Kunder,** välj **Alla kunder**.
1. För den nyskapade kunden klickar du **Redigera**.
1. Klicka **Beställningar** i panelen till vänster.

<u>Förväntat resultat</u>:

Den senast skickade ordern visas i rutnätet.

<u>Faktiskt resultat</u>:

Rutnätet för beställningar visas inte. En tom sida visas i stället.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[Ladda ned MDVA-7868\_EE\_2.2.1\_v1\_Composer.patch](assets/MDVA-7868_EE_2.2.1_v1_composer.patch.zip)

### Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce lokal 2.2.1

Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce i molninfrastruktur från 2.2.0 till 2.2.3
* Adobe Commerce lokal 2.2.0 och 2.2.2 till 2.2.3

## Så här sätter du på plåstret

Se [Använda en kompositkorrigering från Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support, för instruktioner.

## Bifogade filer
