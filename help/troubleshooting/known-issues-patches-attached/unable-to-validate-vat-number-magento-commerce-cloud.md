---
title: Det går inte att validera momsregistreringsnumret - Adobe Commerce i molninfrastrukturen
description: Den här artikeln innehåller en korrigeringsfil för problemet där ett fel uppstår vid verifiering av momsregistreringsnummer.
exl-id: 9868e888-bad8-4823-acab-4b3804933cb0
feature: Cloud, Customer Service, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Det går inte att validera momsregistreringsnumret - Adobe Commerce i molninfrastrukturen

Den här artikeln innehåller en korrigeringsfil för problemet där ett fel uppstår vid verifiering av momsregistreringsnummer.

## Berörda produkter och versioner

Alla Adobe Commerce lokala versioner och Adobe Commerce på molninfrastrukturversioner upp till 2.3.6 (inklusive 2.3.5-p1) påverkades, inklusive redan släppta p1- och p2-versioner. Detta omfattar följande:

* 2.3.5-p1
* 2.3.5
* 2.3.4 - 2.3.4-p2
* 2.3.3 - 2.3.3-p1
* 2.3.2 -2.3.2-p2
* 2.0.0 - 2.3.1

## Problem

<u>Steg som ska återskapas:</u>

1. Gå till **Lager** > **Konfiguration** > **Kunder** > **Kundkonfiguration** > **Skapa nya kontoalternativ** och ange **Aktivera automatisk tilldelning** till **Kundgrupp** till *Ja*.
1. Gå till **Allmänt** > **Butiksinformation** > och ange ett giltigt lands- och momsregistreringsnummer.
1. Klicka på **Validera momsregistreringsnummer**.

<u>Förväntat resultat:</u>

Verifieringen är klar.

<u>Faktiskt resultat:</u>

Följande fel visas: &quot;*Fel vid verifiering av momsregistreringsnummer.*&quot;

## Lösning

Använd [patch](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip) enligt denna artikel.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[MDVA-27623\_EE\_2.3.2-p2\_COMPOSER\_v1.patch](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip)

## Så här sätter du på plåstret

Se [Använda en kompositkorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) för instruktioner.

## Bifogade filer
