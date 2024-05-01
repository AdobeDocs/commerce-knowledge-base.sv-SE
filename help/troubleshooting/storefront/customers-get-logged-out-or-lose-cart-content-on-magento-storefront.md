---
title: Kunderna loggas ut eller förlorar kundvagnsinnehåll på Adobe Commerce store
description: Den här artikeln innehåller en lösning och en lösning på problemet, där kunderna loggas ut eller förlorar artiklar från kundvagnen i butiken, efter att ha omdirigerats till Adobe Commerce Store från betalning eller andra tjänster från tredje part (sessionscookie"försvinner").
exl-id: 9175570c-b06c-4a65-b8ca-7a12ff266afb
feature: Orders, Page Content, Shopping Cart, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# Kunderna loggas ut eller förlorar kundvagnsinnehåll på Adobe Commerce store

Den här artikeln innehåller en lösning på problemet, där kunderna loggas ut eller förlorar artiklar från kundvagnen i butiken, efter att ha omdirigerats till Adobe Commerce Store från betalning eller andra tjänster från tredje part (sessionscookie&quot;försvinner&quot;).

## Berörda produkter och versioner

* Adobe Commerce lokalkontor [alla versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Adobe Commerce om molninfrastruktur, [alla versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

<u>Steg som ska återskapas:</u>

1. Kunden lägger till produkter i varukorgen i butiken och fortsätter till kassan.
1. Kunden omdirigeras till tredje parts webbplats för betalning/leverans eller annan information/tjänst.
1. Kunden omdirigeras tillbaka till butiken.

<u>Faktiskt resultat:</u>

Kunden omdirigeras till den tomma kundvagnen eller en tom sida.

<u>Förväntat resultat:</u>

Kunden omdirigeras till en sida för slutförd betalning (eller annan framgångssida), utan att förlora utcheckningsdata och framsteg.

## Orsak

Samma webbplats-cookie-attributet är inställt på *Lax* eller inte specificerad (som behandlas som inställd på *Lax* ). Med `SameSite` = *Lax* inaktiverar överföring av en cookie till externa URL:er via `POST` förfrågningar.

## Lösning

Kontakta tredjeparts tjänsteleverantör och be deras utvecklare att uppdatera sina integreringar för att konfigurera cookie-parametrar för att lösa problemet.

## Relaterad läsning

[Chrome SameSite-uppdatering](https://www.chromestatus.com/feature/5088147346030592)
