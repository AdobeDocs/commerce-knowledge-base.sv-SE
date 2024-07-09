---
title: Komponentberoenden i konflikt
description: I den här artikeln finns en lösning för komponentberoenden i konflikt. När du försöker installera eller uppdatera Adobe Commerce med hjälp av webbinstallationsguiden visas felmeddelandet *"Komponentberoenden i konflikt"* Composer.
exl-id: 782049c4-b6e1-4ead-a00f-80d2aa8475c9
feature: Configuration
role: Developer
source-git-commit: 8f0f7412e75e07a22e66236b88c095c698dbf23e
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# Komponentberoenden i konflikt

I den här artikeln finns en lösning för komponentberoenden i konflikt. När du försöker installera eller uppdatera Adobe Commerce med hjälp av webbinstallationsguiden visas *&quot;Vi hittade komponentberoenden i konflikt&quot;* Felmeddelande för disposition.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.2.x, 2.3.x
* Adobe Commerce om molninfrastruktur 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x


## Problem {#issue}

Ett felmeddelande om komponentberoenden i konflikt som liknar följande (faktiska paketnamn och versioner varierar):

```bash
We found conflicting component dependencies.
You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
We have detected conflicts with the following packages:
- magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

## Orsak

Det här meddelandet visas om Composer inte kan avgöra vilka komponenter som ska installeras eller uppdateras.

## Lösning

Två huvudscenarier kan leda till komponentberoenden i konflikt. Klicka på ditt scenario för att få felsökningssteg.

* [Uppgraderar Adobe Commerce](#upgrading-magento)
* [Inkompatibilitet med tredjepartsmoduler:](#incompatibility-third-party-modules)
   * [Adobe Commerce (alla distributionstyper)](#magento-commerce-magento-commerce-cloud)
   * [Magento Open Source](#opensource)

## Uppgraderar Adobe Commerce {#upgrading-magento}

Om du uppgraderar Adobe Commerce till molninfrastruktur kan du försöka med följande för att lösa komponentberoenden i konflikt:

* Kontrollera vilka nycklar som används för att uppgradera. Genereras nycklarna från rätt e-postkonto?
* Kontrollera behörigheterna och se till att de överensstämmer med uppgraderingskraven för Magento. Granska [Magento Upgrade Overview > Update and Upgrade Checklist > File System Permissions](https://devdocs.magento.com/guides/v2.3/comp-mgr/prereq/prereq_compman-checklist.html#perms) i vår dokumentation för utvecklare.

## Inkompatibilitet med tredjepartsmoduler: {#incompatibility-third-party-modules}

Komponentberoenden i konflikt kan också orsakas av tredjepartsmoduler som är beroende av tidigare Commerce-komponenter än de som du har installerat. Försök med följande:

1. I föregående [exempel](#issue)går det inte att uppgradera den installerade paketet magento/sample-data version 0.74.0-beta15 till 1.0.0-beta. 0.74.0-beta15 kan dock uppgraderas till 0.74.0-beta16 (eller andra). Redigera `composer.json` om du vill göra någon av dessa ändringar. Vanligtvis definieras de versioner som ditt projekt begär i `require` eller `require-dev` -egenskapen för objektet i den JSON-filen. Beroende på vilka alternativ som finns för de paketversioner som tillhandahålls, kan det hända att de anger en specifik version eller en begränsning. Allmän vägledning om hur du använder Composer finns i vår molninfrastruktur i [Cloud for Adobe Commerce > Technologies and Requirements > Composer](https://devdocs.magento.com/cloud/reference/cloud-composer.html#files) i vår dokumentation för utvecklare. Om du använder Adobe Commerce lokalt kan du läsa [Adobe Commerce > Installationshandbok > Installera Adobe Commerce med Composer](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html) .
1. Prova beredskapskontrollen nu. Granska [Adobe Commerce Upgrade Overview > Run the Module Manager > Step 1 Readiness Check](https://devdocs.magento.com/guides/v2.3/comp-mgr/module-man/compman-readiness.html) i vår dokumentation för utvecklare.
1. Om beredskapskontrollen misslyckas med ett annat felmeddelande om komponentberoende, klicka på följande länkar beroende på om du använder [Adobe Commerce](#magento-commerce-magento-commerce-cloud) eller [Magento Open Source](#opensource) om du vill få fler felsökningssteg.

## Adobe Commerce {#magento-commerce-magento-commerce-cloud}

1. Kontakta utvecklaren av tillägget så att de kan hjälpa dig. Kontaktinformationen för dem finns på sidan som du köpte tillägget från på Commerce Marketplace. Leta efter **Kontakta återförsäljare** på den högra panelen. Alla Commerce-utvecklare måste tillhandahålla användar- och installationshandböcker när de publicerar ett tillägg på Marketplace. Du hittar båda till höger på landningssidan.
1. Om du inte får något svar från säljaren inom rimlig tid, vänligen [kontakta Marketplace Support](mailto:commercemarketplacesupport@adobe.com) så att vi kan påminna dem om deras kundsupportåtaganden.

## Magento Open Source {#opensource}

Begär assistans på [vårt huvudforum](https://community.magento.com/) eller [kontakta en Adobe Commerce-partner](https://magento.com/find-a-partner) som är till hjälp vid Öppna Source-utgåvor.
