---
title: Leveransadressen har inte sparats efter siduppdatering vid utcheckning
description: Den här artikeln innehåller en patch för det kända Adobe Commerce 2.2.3-problemet där kundens redan ifyllda leveransadressformulär var tomt igen efter att webbläsarsidan uppdaterats vid gästutcheckning. Problemet uppstod när den beständiga kundvagnen aktiverades.
exl-id: b757e4af-7b1a-41bc-8460-9a6858c7aa5e
feature: Checkout, Orders, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Leveransadressen har inte sparats efter siduppdatering vid utcheckning

Den här artikeln innehåller en patch för det kända Adobe Commerce 2.2.3-problemet där kundens redan ifyllda leveransadressformulär var tomt igen efter att webbläsarsidan uppdaterats vid gästutcheckning. Problemet uppstod när den beständiga kundvagnen aktiverades.

## Problem

Kunderna går igenom gästutcheckningen och fyller i alla formulär inklusive leveransadressen. De kommer till avsnittet Granska och betalningar och läser in sidan igen. Formuläret är tomt och måste ange leveransadressen igen. Beständig kundvagnsfunktion är aktiverad.

<u>Steg som ska återskapas</u> :

**Förutsättningar**: Den beständiga kundvagnsfunktionen är aktiverad. Kontrollera om det är aktiverat i Admin, under **Lager** > **Konfiguration** > **Kunder** eller **Lager** > **Konfiguration** > **Försäljning** beroende på vilken version av Adobe Commerce du har.

1. Gå till butiken.
1. Lägg produkter i kundvagnen.
1. Gå till kassan som gäst.
1. Fyll i leveransadressen, välj leveransalternativ och fortsätt att säkra betalningen.
1. Omdirigeras till avsnittet Granskning och betalningar i kassan.
1. Kontrollera att du ser leveransadressen i avsnittet Leverera till.
1. Uppdatera sidan.

<u>Förväntat resultat</u>:

Du kan fortsätta utcheckningen och alla data sparas.

<u>Faktiskt resultat</u>:

Leveransadressen är tom, du måste ange den igen.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[Hämta MDVA-9718\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-9718_EE_2.2.3_COMPOSER_v1.patch.zip)

### Kompatibla Adobe Commerce-versioner

**Korrigeringen skapades för:**

* Adobe Commerce 2.2.3

**Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:**

* Adobe Commerce om molninfrastruktur 2.1.13 - 2.1.18
* Adobe Commerce om molninfrastruktur 2.2.0 - 2.2.5
* Adobe Commerce lokal 2.0.X
* Adobe Commerce lokal 2.1.X
* Adobe Commerce lokal 2.2.0 - 2.2.2 och 2.2.4 - 2.2.5

## Så här sätter du på plåstret

Instruktioner finns i [Använda en kompositkorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.

## Bifogade filer
