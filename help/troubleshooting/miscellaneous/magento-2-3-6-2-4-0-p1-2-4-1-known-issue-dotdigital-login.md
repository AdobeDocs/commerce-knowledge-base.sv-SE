---
title: "Adobe Commerce 2.3.6, 2.4.0-p1, 2.4.1 known issue: dotdigital login"
description: I den här artikeln beskrivs ett känt fel i Adobe Commerce 2.3.6, 2.4.0-p1 och 2.4.1 där det är omöjligt att logga in på [dotdigital](https://dotdigital.com/) via adminpanelen när det digitala kontot är aktiverat.
exl-id: 427d895c-8c03-4ced-813a-eeaa67f1d1f0
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Adobe Commerce 2.3.6, 2.4.0-p1, 2.4.1 Känt fel: dotdigital inloggning

I den här artikeln beskrivs ett känt fel i Adobe Commerce 2.3.6, 2.4.0-p1 och 2.4.1 där det är omöjligt att logga in på [dotdigital](https://dotdigital.com/) via panelen Admin när det digitala kontot är aktiverat.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur och Adobe Commerce lokalt 2.3.6 (endast Safari-webbläsare)
* Adobe Commerce i molninfrastrukturen och Adobe Commerce lokalt 2.4.0-p1 (endast Safari-webbläsaren)
* Adobe Commerce om molninfrastruktur och Adobe Commerce lokal 2.4.1 (endast Safari-webbläsare)

## Problem

<u>Förutsättningar</u>:

1. dotdigital-konto finns.
1. Giltiga autentiseringsuppgifter för Dtdigital API finns i Adobe Commerce.

<u>Steg som ska återskapas</u>:

1. Gå till **Lager** > **Konfiguration** > **DOTDIGITAL** > **Chattinställningar** > **Aktiverad** är inställd på *Ja.*
1. Klicka på **Konfigurera** in **Konfigurera chattwidget** eller **Konfigurera chattteam**.

<u>Förväntade resultat</u>:

Chattinställningssidan ska öppnas via administratörspanelen.

<u>Faktiska resultat</u>:

Det går inte att logga in på dotdigital.

## Lösning

Tillfällig lösning: använd en annan webbläsare än Safari för just den här situationen.

## Relaterad läsning

[Adobe Commerce 2.4.1 Känt fel - Vertex-adressen kan inte valideras med olika leverans-/faktureringsadresser](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md) i vår kunskapsbas för support.
