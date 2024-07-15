---
title: PHP-versionsfel eller 404-fel vid åtkomst till Adobe Commerce i webbläsaren
description: I den här artikeln beskrivs lösningar på problem där du inte kan komma åt din Adobe Commerce-instans i en webbläsare och få felmeddelanden om 404 eller"PHP-version som inte stöds".
exl-id: 6cfdeaae-5e52-411c-9006-5af8a467873a
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# PHP-versionsfel eller 404-fel vid åtkomst till Adobe Commerce i webbläsaren

I den här artikeln beskrivs lösningar på problem där du inte kan komma åt din Adobe Commerce-instans i en webbläsare och få felmeddelanden om 404 eller&quot;PHP-version som inte stöds&quot;.

## Berörda produkter och versioner:

* Adobe Commerce 2.3.x

## Problem: PHP-versionen stöds inte

Följande meddelande visas när du försöker få åtkomst till Adobe Commerce storefront eller Commerce Admin:

`Magento supports PHP 7.1.3 or later. Please read Magento System Requirements.`

### Lösning

Försök med följande:

* Uppgradera PHP till version 7.3. Mer information finns i [Krav för Adobe Commerce 2.3-teknikhög](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements.html#php) i utvecklardokumentationen.
* Starta om Apache eftersom den kanske inte använder samma PHP-version som i filsystemet. Använd följande kommandon om du vill starta om Apache:
   * Ubuntu: `service apache2 restart`
   * CentOS: `service httpd restart`

## Problem: fel 404

Ett 404-fel (Hittades inte) visas när du försöker få åtkomst till Adobe Commerce storefront eller Commerce Admin.

### Lösning

Försök med följande:

* Kontrollera att [Omskrivningar av Apache-servern](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/apache.html) är aktiverade. Om omskrivningar från Apache-servern är felaktigt inställda kommer statiska filer inte att hanteras från rätt plats.
* Det kan vara problem med den bas-URL som du angav under installationen. Du anger bas-URL:en som värdet för `--base-url=` när du installerar Adobe Commerce från kommandoraden eller som värdet för fältet **Din butiksadress** på webbkonfigurationssidan i webbinstallationsprogrammet. Bas-URL:en *måste* börja med schemat (till exempel `http://` ) och sluta med ett avslutande snedstreck (/). Kör installationsprogrammet igen med ett giltigt värde och försök sedan komma åt Adobe Commerce.
