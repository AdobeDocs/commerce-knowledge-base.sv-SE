---
title: Fel på tom sida eller omdirigeringsslinga vid åtkomst till storefront eller Commerce Admin
description: Den här artikeln innehåller en lösning på problemet när du öppnar Adobe Commerce storefront eller backend och får en tom sida eller omdirigeringsslinga.
exl-id: 65869de2-1939-481b-844b-69122345b407
feature: Admin Workspace, Cache, Storefront
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# Fel på tom sida eller omdirigeringsslinga vid åtkomst till storefront eller Commerce Admin

Den här artikeln innehåller en lösning på problemet när du öppnar Adobe Commerce storefront eller backend och får en tom sida eller omdirigeringsslinga.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur, alla versioner
* Adobe Commerce lokala, alla versioner
* Magento Open Source, alla versioner

## Problem

<u>Steg som ska återskapas</u>

Öppna en butiks- eller administratörssida.

<u>Förväntat resultat</u>

Sidan öppnas.

<u>Faktiskt resultat</u>

Sidan är tom eller visar *&quot;Den här webbsidan har en omdirigeringsslinga&quot;* felmeddelande.

## Orsak

En av de troligaste orsakerna till problemet är att Adobe Commerce är inställt på omdirigering från osäker URL till säker URL, men en osäker URL anges som värde för den säkra URL-inställningen.

För att åtgärda problemet måste du korrigera värdet på den säkra länken.

## Lösning

Så här ser du till att det är orsaken till problemet:

1. Kontrollera `web/secure/enable_upgrade_insecure` , `web/secure/use_in_adminhtml` (om du har problem med omdirigering av blank/loop i Admin) eller `web/secure/use_in_frontend` (om du har omdirigeringsutgåvan blank/loop på butikens framsida) i `'core_config_data'` Databastabell.
   * If `web/secure/enable_upgrade_insecure` är inställd på &quot;1&quot;, ställs Adobe Commerce in för att lägga till svarshuvudet `Content-Security-Policy: upgrade-insecure-requests`, vilket innebär att webbläsare instrueras att använda HTTPS och att omdirigera alla frågor som kommer över HTTP till HTTPS, både för Admin och för storefront.
   * If `web/secure/use_in_adminhtml` är inställd på &quot;1&quot;, returnerar Adobe Commerce HTTPS-omdirigeringar för alla HTTP-begäranden för administratörssidorna.
   * If `web/secure/use_in_frontend` är inställd på &quot;1&quot;, returnerar Adobe Commerce HTTPS-omdirigeringar för alla HTTP-begäranden för butikens frontsidor.
1. Kontrollera `web/secure/base_url` och `web/unsecure/base_url` värden i `'core_config_data'` tabell. Om båda börjar med    `http`måste du korrigera det säkra värdet.

Åtgärda problemet:

1. Ange värdet som börjar med `https` for `web/secure/base_url.`
1. Rensa konfigurationscachen genom att köra följande kommando för att ändringarna ska tillämpas:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```
