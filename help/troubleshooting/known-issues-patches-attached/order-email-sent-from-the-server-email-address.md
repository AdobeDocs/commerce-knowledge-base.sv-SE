---
title: E-postbeställning har skickats från serverns e-postadress
description: I de här artiklarna finns en patch för det kända problemet med Adobe Commerce om molninfrastruktur 2.2.4 som rör e-postbeställningar som skickas från serverns e-postadress.
exl-id: f32e0c09-e19e-4269-bbba-0533d74a7f49
feature: Communications
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# E-postbeställning har skickats från serverns e-postadress

I de här artiklarna finns en patch för det kända problemet med Adobe Commerce om molninfrastruktur 2.2.4 som rör e-postbeställningar som skickas från serverns e-postadress.

## Problem

E-postmeddelanden med orderbekräftelse skickas från Apache-serverns e-postadress. Andra e-postmeddelanden (glömt lösenord och så vidare) skickas från de konfigurerade e-postadresserna.

<u>Steg som ska återskapas</u>:

1. Gör en beställning med **Skicka orderbekräftelse** är markerad.
1. Kontrollera e-post.

<u>Förväntat resultat</u>:

E-postmeddelandet skickades från den Adobe Commerce-konfigurerade avsändaradressen.

<u>Faktiskt resultat</u>:

E-postmeddelandet skickades från den e-postadress som konfigurerats i Apache-servern som används.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[Ladda ned MDVA-10993\_EE\_2.2.4\_v1.comser.patch](assets/MDVA-10993_EE_2.2.4_v1.composer.patch.zip)

### Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce i molninfrastruktur 2.2.4

Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce i molninfrastruktur 2.2.5
* Adobe Commerce om molninfrastruktur 2.2.6
* Adobe Commerce om molninfrastruktur 2.2.7
* Adobe Commerce om molninfrastruktur 2.2.8
* Adobe Commerce lokal 2.2.4
* Adobe Commerce lokal 2.2.5
* Adobe Commerce lokal 2.2.6
* Adobe Commerce lokal 2.2.7
* Adobe Commerce lokal 2.2.8
* Adobe Commerce lokal 2.3.0

## Så här sätter du på plåstret

Instruktioner finns i [Använda en kompositkorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.

## Bifogade filer
