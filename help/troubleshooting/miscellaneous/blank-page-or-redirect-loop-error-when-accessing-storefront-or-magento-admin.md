---
title: Fel på tom sida eller omdirigeringsslinga vid åtkomst till storefront eller Commerce Admin
description: Den här artikeln innehåller en lösning på problemet när du öppnar Adobe Commerce storefront eller backend och får en tom sida eller omdirigeringsslinga.
exl-id: 65869de2-1939-481b-844b-69122345b407
feature: Admin Workspace, Cache, Storefront
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '354'
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

Sidan är tom eller visar felmeddelandet *&quot;Den här webbsidan har en omdirigeringsslinga&quot;*.

## Orsak

En av de troligaste orsakerna till problemet är att Adobe Commerce är inställt på omdirigering från osäker URL till säker URL, men en osäker URL anges som värde för den säkra URL-inställningen.

För att åtgärda problemet måste du korrigera värdet på den säkra länken.

## Lösning

Så här ser du till att det är orsaken till problemet:

1. Kontrollera värdet `web/secure/enable_upgrade_insecure`, `web/secure/use_in_adminhtml` (om du har omdirigeringsutgåvan blank/loop i Admin) eller `web/secure/use_in_frontend` (om du har omdirigeringsutgåvan blank/loop på butikens framsida) i databastabellen `'core_config_data'`.
   * Om `web/secure/enable_upgrade_insecure` är inställt på 1, är Adobe Commerce inställt på att lägga till svarshuvudet `Content-Security-Policy: upgrade-insecure-requests`, vilket instruerar webbläsare att använda HTTPS och omdirigerar alla frågor som kommer via HTTP
till HTTPS, både för Admin och storefront.
   * Om `web/secure/use_in_adminhtml` är inställt på 1 returnerar Adobe Commerce HTTPS-omdirigeringar för alla HTTP-begäranden för administratörssidorna.
   * Om `web/secure/use_in_frontend` är inställt på 1 returnerar Adobe Commerce HTTPS-omdirigeringar för alla HTTP-begäranden för butikens frontsidor.
1. Kontrollera värdena `web/secure/base_url` och `web/unsecure/base_url` i tabellen `'core_config_data'`. Om båda börjar med    `http`, måste du korrigera det säkra värdet.

Åtgärda problemet:

1. Ange värdet från `https` för `web/secure/base_url.`
1. Rensa konfigurationscachen genom att köra följande kommando för att ändringarna ska tillämpas:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

## Relaterad läsning

[Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
