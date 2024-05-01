---
title: Felsöka problem med snabbutcheckning
description: I den här artikeln beskrivs problem som kan uppstå när du använder tillägget Snabbutcheckning för Adobe Commerce och lösningar på dessa problem så att du kan använda tillägget.
exl-id: 8ab46318-d62a-4b7e-bbe5-4c52cfeb9e36
feature: Checkout, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Felsöka problem med snabbutcheckning

I den här artikeln beskrivs problem som kan uppstå när du använder tillägget Snabbutcheckning för Adobe Commerce och lösningar på dessa problem så att du kan använda tillägget.

## Berörda produkter och versioner

* The [Snabbutcheckning](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/overview.html) är kompatibelt med både Magento Open Source och Adobe Commerce. Se [Livscykelprincip](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html) om du vill ha mer information om vilka versioner som stöds.

## Felaktiga dispositionsnycklar och minimala stabilitet för att `RC`

<u>Orsak</u>:

Om följande felmeddelande visas kan det finnas felaktiga dispositionsnycklar:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

<u>Lösning</u>:

Kontrollera att dispositionsnycklarna är länkade till _MAGENTO ID_ som används vid registreringen av snabbutcheckning.

Så här ser du vilka dispositionsnycklar som är konfigurerade:

1. Hitta platsen för `auth.json` fil:

   ```bash
   composer config --global home
   ```

1. Visa `auth.json` fil:

   ```bash
   cat /path/to/auth.json
   ```

1. Se [vilka tangenter som är kopplade till ditt Magento-ID](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

1. Ange lägsta stabilitet till `RC` i `composer.json` -fil.

   ```json
   "minimum-stability": "RC"
   ```

## Inte tillräckligt med minne för PHP

<u>Orsak</u>:

Om följande felmeddelande visar att du inte har tillräckligt med minne för PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

<u>Lösning</u>:

[Öka minnesgränsen](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) för PHP i din miljö i `php.ini`.

Du kan också ange minnesgränsen med det här kommandot: `php -d memory_limit=-1 [path to composer]/composer require magento/quick-checkout`.

Exempel:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/quick-checkout
```

## Lägg till gatuadressrader med en ny leveransadress

Det finns ett känt fel för tillägget Snabbutcheckning.

När du [logga in med ett bolt-konto](https://help.bolt.com/shoppers/guides/checkout/log-in/)kan du lägga till en ny leveransadress med en begränsning på 4 rader per gatuadress.

Om den nya leveransadressen innehåller fler än fyra rader lagras de inte.

Adobe Commerce kan vanligtvis konfigureras för att stödja upp till 20 gatuadressrader.

## Oväntat beteende när `Display Billing Address On` är inställd på `payment page`

Det finns ett känt fel för tillägget Snabbutcheckning.

Om du anger `Display Billing Address On` parametern till `payment page` och [logga in med ett bolt-konto](https://help.bolt.com/shoppers/guides/checkout/log-in/) när du markerar `My billing and shipping address are the same` kryssruta, alternativknappen visas `use existing card`. Eftersom faktureringsadressen endast gäller för nya kreditkort, kommer adressen inte att vara synlig förrän användaren i Bult bestämmer sig för att lägga till ett nytt kreditkortsalternativ.

Se [Utcheckning](https://docs.magento.com/user-guide/configuration/sales/checkout.html) för mer information om `Display Billing Address On` parameter.
