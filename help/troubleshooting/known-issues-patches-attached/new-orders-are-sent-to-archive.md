---
title: Nya order skickas till arkivet
description: I den här artikeln finns en patch för det kända Adobe Commerce 2.2.0-problemet som gäller nyligen skapade order som visas i arkivet i stället för i beställningsrutnätet i Commerce Admin.
exl-id: 37b70d28-0569-44f2-b677-29b2bde0bc5c
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Nya order skickas till arkivet

I den här artikeln finns en patch för det kända Adobe Commerce 2.2.0-problemet som gäller nyligen skapade order som visas i arkivet i stället för i beställningsrutnätet i Commerce Admin.

>[!NOTE]
>
>Felet korrigerades i 2.2.3 och senare.

## Problem

När kunderna lägger order visas de i rutnätet för arkiverade order istället för i rutnätet för vanliga order.

<u>Steg som ska återskapas</u>:

1. Lägg valfri produkt i kundvagnen, gå vidare till kassan och lägg ordern.
1. Gå till **Försäljning** > **Åtgärder** > **Beställning** i Commerce Admin. Se ordningen i rutnätet.
1. Navigera till **Försäljning** > **Arkiv** > **Beställningar**. Se den nya ordningen i rutnätet.

<u>Förväntade resultat</u>:

Ordningen visas endast i rutnätet för beställningar.

<u>Faktiska resultat</u>:

Ordningen visas i rutnätet för beställningar och i orderarkivrutnätet.

## Lösning

När du har använt korrigeringen visas ordningarna i rutnätet som förväntat. Men du måste manuellt återställa de som skickades till arkivet innan korrigeringen tillämpades i Commerce Admin.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[Ladda ned MDVA-8007\_EE\_2.2.0\_v1.comser.patch](assets/MDVA-8007_EE_2.2.0_v1.composer.patch.zip)

### Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce 2.2.0

Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce lokalt, Adobe Commerce om molninfrastruktur 2.2.1 - 2.2.3

## Så här sätter du på plåstret

Instruktioner finns i [Använda en dispositionsruta som tillhandahålls av Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.

## Användbara länkar i vår användarhandbok

* [Hantera arkiverade order](https://docs.magento.com/user-guide/sales/order-archive.html)

## Bifogade filer
