---
title: Felsök installationen av betaltjänster
description: I den här artikeln förklaras de fel som kan uppstå när du installerar betaltjänster, och här beskrivs lösningar för att åtgärda felen så att du kan slutföra installationen.
exl-id: 0aef7482-8834-400e-85b9-d3d3eb0ab76e
feature: Install, Orders, Payments, Saas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# Felsök installationen av betaltjänster

I den här artikeln förklaras de fel som kan uppstå när du installerar betaltjänster, och här beskrivs lösningar för att åtgärda felen så att du kan slutföra installationen.

## Berörda produkter och versioner

* [Betalningstjänster](https://marketplace.magento.com/magento-payment-services.html) är nu kompatibelt med Adobe Commerce version 2.4.0 till 2.4.4.

## Problem - Felaktiga dispositionsnycklar

När du installerar tillägget Betalningstjänster kan ett felmeddelande visas om att du använde felaktiga dispositionsnycklar under installationen.

<u>Steg som ska återskapas</u>:

1. Försök att [installera betalningstjänsterna](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html).
1. Se följande fel:

   *Det gick inte att hitta en matchande version av paketets magento/payment-services. Kontrollera paketstavningen, versionens begränsning och att paketet är tillgängligt i en stabilitet som matchar minimistabiliteten (stabil).*

<u>Förväntat resultat</u>:

Du kan följa dessa [installationsanvisningar](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) i utvecklardokumentationen för att installera betaltjänster.

<u>Faktiskt resultat</u>:

Under installationen visas ett felmeddelande om att du inte använde rätt Composer-nycklar under installationen.

### Orsak

Du använde felaktiga dispositionsnycklar under installationen.

### Lösning

Kontrollera att [dina dispositionsnycklar är länkade till det Magento-ID](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html#incorrect-composer-keys) som användes vid registreringen av betalningstjänsterna.

## Problem - Använda samma dataspace i flera instanser

Kör en konfiguration för flera miljöer med betaltjänster på varje.

### Lösning

Samma API-nyckel kan användas för alla instanser, men varje instans måste använda sin egen SaaS-dataminne.

När du skapar ett SaaS-projekt genererar Commerce ett eller flera SaaS-datamallar beroende på din Commerce-licens:

* Adobe Commerce - ett produktionsdatautrymme; två testdatautrymme
* Magento Open Source - Ett produktionsdatautrymme utan testdatautrymme

Följ anvisningarna i [Commerce API-nyckel och privat nyckel](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#obtain-api-credentials) för att konfigurera ditt betaltjänsttillägg.

## Problem - Det finns inte tillräckligt med minne för PHP

När du installerar tillägget Betalningstjänster kan ett felmeddelande visas som anger att du inte har tillräckligt med minne för PHP.

<u>Steg som ska återskapas</u>:

1. Försök att [installera betalningstjänsterna](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html).
1. Se följande fel eller liknande:

   *Allvarligt fel: Den tillåtna minnesstorleken på 2146435072 byte är slut (försök gjordes att allokera 4096 byte) i phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php på rad 52.*

<u>Förväntat resultat</u>:

Du kan följa dessa [installationsanvisningar](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) i utvecklardokumentationen för att installera betaltjänster.

<u>Faktiskt resultat</u>:

Under installationen visas ett felmeddelande om att du inte har tillräckligt med minne för PHP.

### Orsak

Gränsvärdet för PHP i din miljö är inte inställt på ett tillräckligt högt tröskelvärde.

### Lösning

[Öka minnesgränsen för PHP](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html#not-enough-memory-for-php) i din miljö i `php.ini`.
