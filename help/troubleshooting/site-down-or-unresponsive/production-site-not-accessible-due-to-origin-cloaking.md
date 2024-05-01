---
title: Webbplatsen är inte tillgänglig på grund av ursprungsinsvepning
description: Den här artikeln innehåller en lösning för när din Adobe Commerce på molninfrastruktur staging eller storefront och/eller Admin inte är tillgänglig.
exl-id: 4412d744-3066-4f78-bc45-8149614ce455
feature: Products
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# Webbplatsen är inte tillgänglig på grund av ursprungsinsvepning

Den här artikeln innehåller en lösning för när din Adobe Commerce på molninfrastruktur staging eller storefront och/eller Admin inte är tillgänglig.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.3.x, 2.4.x

## Problem

/mydomain.com.c.&lt;projectid>.magento.cloud/ är inte längre tillgänglig.

<u>Steg som ska återskapas:</u>

1. Logga in på ditt projekt.
1. Klicka **Åtkomstprojekt** för en lista över URL:er och SSH.

<u>Faktiska resultat:</u>

Sidan läses inte in med följande fel:

*NET::ERR\_CERT\_INVALID*  *TLS-varning, felaktigt certifikat (554):*

<u>Förväntade resultat:</u>

Sidan har lästs in.

## Orsak

Insvepning av ursprung har aktiverats, så det går inte längre att komma åt origo direkt.

Insvepning är en säkerhetsfunktion som gör det möjligt för Adobe Commerce att blockera all trafik som inte går snabbt till molninfrastrukturen (ursprung) för att förhindra DDoS-attacker.

## Lösning

* Om din molnsajt är aktiv växlar du till https://mydomain.com/.
* Om du har en aktiv plats (ej molnet), använder du domänen https://mydomain.com/, konfigurerar du en underdomän `mcprod.mydomain.com` och uppdatera **Bas-URL** till *https://mcprod.mydomain.com* i stället, [peka DNS snabbt](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#update-dns-configuration-with-development-settings).

## Relaterad läsning

[Vanliga frågor och svar om insvepning med snabb ursprung](/help/faq/general/fastly-origin-cloaking-enablement-faq.md) i vår kunskapsbas för support.
