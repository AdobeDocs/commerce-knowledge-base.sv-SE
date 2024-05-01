---
title: Cybersource-betalning från Admin och framåt i olika domäner har inte bearbetats
description: I den här artikeln finns en patch för den kända Adobe Commerce 2.3.0-begränsningen som handlar om att inte kunna bearbeta Cybersource-betalningar från både storefront och Commerce Admin, om de finns i olika domäner.
exl-id: 948d5907-70bd-4890-bc8a-23e04b116018
feature: Admin Workspace, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# Cybersource-betalning från Admin och framåt i olika domäner har inte bearbetats

I den här artikeln finns en patch för den kända Adobe Commerce 2.3.0-begränsningen som handlar om att inte kunna bearbeta Cybersource-betalningar från både storefront och Commerce Admin, om de finns i olika domäner.

>[!NOTE]
>
>Adobe Commerce Cybersource-betalningsintegration har tagits bort sedan 2.3.3 och kommer att tas bort helt i 2.4.0. Använd [officiell förlängning](https://marketplace.magento.com/cybersource-global-payment-management.html) från Marketplace istället.

## Problem

Den tidigare implementeringen av Cybersource-integreringen tillät endast bearbetning av betalningar från en domän. Om din Adobe Commerce-butik finns på en annan domän än Commerce Admin får du därför följande fel när du försöker göra en beställning med Cybersource i Admin: &quot; *Inläsning nekad av X-Frame-Options: https://%your\_domain%/cybersource/SilentOrder/TokenResponse/ tillåter inte bildrutning mellan ursprung.* ...&quot;

<u>Steg som ska återskapas</u>:

1. Konfigurera Admin för en annan underdomän.
1. Konfigurera Cybersource för butiken under **Lager** > Inställningar > **Konfiguration** > **Försäljning** > **Betalningsmetoder** > **CyberSource**.
1. Gå till **Försäljning** > **Beställningar**.
1. Skapa ny order.
1. Skapa ny kund.
1. Ange kundinformation.
1. Ange orderinformation (produkter, leveranssätt).
1. Välj Cybersource som betalningsmetod.
1. Skicka beställning.

<u>Förväntat resultat</u>: Beställningen är utan problem.

<u>Faktiskt resultat</u>: På sidan Ordning visas en inläsningsikon, men ordningen placeras aldrig. Felet visas i konsolen.

## Lösning

Den bifogade korrigeringen förbättrar integrationen med Cybersource. När du har implementerat korrigeringen måste du skapa en till profil med Cybersource för att bearbeta betalningar i Admin och lägga till de nödvändiga inloggningsuppgifterna i Cybersource-konfigurationen i Commerce Admin under **Lager** > Inställningar > **Konfiguration** > **Försäljning** > **Betalningsmetoder** > **CyberSource**.

>[!NOTE]
>
>Förbättringen ingår i Adobe Commerce lokala infrastruktur och molninfrastruktur 2.2.9 och 2.3.1.

## Lappa

Det finns flera patchar kopplade till den här artikeln, olika patchar för olika versioner. Om du vill hämta en patch rullar du nedåt till slutet av artikeln och klickar på filnamnet, eller klickar på följande länk:

* [Hämta MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch](assets/MDVA-5914_EE_2.1.9_COMPOSER_v3.patch.zip)
* [Hämta MDVA-8609\_EE\_2.2.2\_COMPOSER\_v2.patch](assets/MDVA-8609_EE_2.2.2_COMPOSER_v2.patch.zip)
* [Hämta MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch](assets/MDVA-12964_EE_2.2.5_COMPOSER_v1.patch.zip)
* [Hämta MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch](assets/MDVA-16643_EE_2.3.0_COMPOSER_v1.patch.zip)

## Kompatibla Adobe Commerce-versioner

Patcharna skapades för en viss version och beskrivs i patchfilens namn. Exempel: MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch skapades för Adobe Commerce 2.1.9 och är den bästa korrigeringsfilen som kan användas för den här versionen.

Patcharna är också kompatibla med följande versioner:

* Adobe Commerce lokal 2.1.3-2.1.17; Adobe Commerce om molninfrastruktur 2.1.5-2.12 (MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch)
* Adobe Commerce lokal 2.2.0-2.2.3; Adobe Commerce on cloud infrastructure 2.2.0-2.2.3 (MDVA-8609\_EE\_2.2.2\_COMPOSER\_v2.patch)
* Adobe Commerce lokal 2.2.4-2.2.7; Adobe Commerce on cloud infrastructure 2.2.4-2.2.7 (MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch)
* Adobe Commerce lokal 2.2.8, 2.3.0; Adobe Commerce on cloud infrastructure 2.3.0 (MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch)

## Så här lägger du på en patch

Instruktioner finns i [Använda en kompositkorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.

## Bifogade filer
