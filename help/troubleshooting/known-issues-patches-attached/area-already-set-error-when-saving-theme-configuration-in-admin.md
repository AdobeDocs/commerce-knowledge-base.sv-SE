---
title: Felet "Område har redan angetts" när temakonfigurationen sparades i Admin
description: I den här artikeln finns en patch för det kända Adobe Commerce-problemet i molninfrastruktur 2.2.4 som handlar om att få felmeddelandet *"Area is already set"* när du försöker ange ett tema för standardbutiksvyn i Commerce Admin.
exl-id: c4e34a73-b774-4447-ba8e-aaf208ad54c5
feature: Admin Workspace, Configuration, Themes
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Felet &quot;Område har redan angetts&quot; när konfigurationen av temat sparades i Admin

I den här artikeln finns en patch för det kända Adobe Commerce-problemet i molninfrastruktur 2.2.4 som rör hämtning av felmeddelandet *&quot;Area is already set&quot;* när du försöker ange ett tema för standardbutiksvyn i Commerce Admin.

## Problem

Du får felmeddelandet *Något gick fel när den här konfigurationen sparades: Området är redan inställt* när du försökte ange ett tema för standardbutiksvyn.

<u>Steg som ska återskapas</u>:

1. Logga in på Commerce Admin.
1. Navigera till **Innehåll** > **Design** > **Konfiguration**.
1. Ange konfigurationsomfånget till *Standardbutiksvy*.
1. Ändra temat i listrutan **Använt tema**. Exempel: från *Luma* till *Tom.*
1. Klicka på **Spara konfiguration**.

<u>Förväntat resultat</u>: Det valda temat används för standardbutiksvyn.

<u>Faktiskt resultat</u> : Temat används inte, *Något gick fel när konfigurationen sparades: Området är redan inställt* visas.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den klickar du på följande länk eller rullar nedåt till slutet av artikeln och klickar på den bifogade filen:

[Hämta MDVA-11106\_EE\_2.2.4\_v1.comser.patch](assets/MDVA-11106_EE_2.2.4_v1.composer.patch.zip)

## Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce i molninfrastruktur 2.2.4

Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce om molninfrastruktur 2.0.X
* Adobe Commerce i molninfrastruktur 2.1.X
* Adobe Commerce om molninfrastruktur 2.2.0 - 2.2.5
* Adobe Commerce lokal 2.0.X
* Adobe Commerce lokal 2.1.X
* Adobe Commerce lokal 2.2.0 - 2.2.5

## Så här sätter du på plåstret

Instruktioner finns i [Använda en dispositionsruta från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.

## Bifogade filer
