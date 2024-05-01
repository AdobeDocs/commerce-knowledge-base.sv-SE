---
title: Distributionsproblem relaterade till kontobehörigheter och åtkomstnycklar
description: Den här artikeln innehåller en lösning på problem med distributionen av Adobe Commerce i molninfrastruktur som orsakas av konflikter i samband med ägarskap av åtkomstnyckel.
exl-id: e8d72ebe-453f-4d18-a25e-c76e685aa667
feature: Deploy, Roles/Permissions
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Distributionsproblem relaterade till kontobehörigheter och åtkomstnycklar

Den här artikeln innehåller en lösning på problem med distributionen av Adobe Commerce i molninfrastruktur som orsakas av konflikter i samband med ägarskap av åtkomstnyckel.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur, alla versioner som stöds

## Problem

<u>Förutsättningar</u>:

Molnlicensen är kopplad till kontakt A (e-postadress: *<u>first@e.mail</u>*)

<u>Steg som ska återskapas</u>:

1. Kontakta en Adobe Commerce-åtkomstnyckel som har skapats på deras konto (tangent X) och installera dem i molnet.
1. Kontakt B (e-postadress: *<u>second@e.mail</u>*) köpte ett tillägg med det här kontot och skapade nycklarna för installation av tillägget (nyckel Y).
1. Kontakta A och lämna företaget och licensen (ägarskapet) överfördes sedan till kontakt B.
1. Systemintegratören försöker installera tillägget i molnmiljön med Key X.

<u>Förväntat resultat</u>:

Tillägget har installerats.

<u>Faktiskt resultat</u>:

Tillägget är inte installerat eftersom distributionen misslyckas.

## Orsak

Båda nycklarna tilldelas till kontaktrollen, vilket orsakar en konflikt.

## Lösning

Om en distribution misslyckas efter att en ändring har gjorts i den primära kontakten på kontot (med både det ursprungliga kontot och det nya kontot som var och en har sina egna nycklar) och nycklarna har överförts från det ursprungliga kontot till det nya kontot, måste du inaktivera nycklarna från det ursprungliga kontot. I exemplet ovan bör tangenten X vara inaktiverad.

### Inaktivera åtkomstnyckeln

Om du inte har tillgång till [Commerce Marketplace](https://marketplace.magento.com/) konto som är associerat med den gamla nyckeln, [kontakta Adobe Commerce support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om du vill inaktivera nyckeln.

Om du har tillgång till det Marketplace-konto som är kopplat till den gamla nyckeln utför du följande steg för att inaktivera nyckeln:

1. Logga in på [Commerce Marketplace](https://marketplace.magento.com/) med inloggningsuppgifterna från det gamla kontot.
1. Klicka på kontonamnet längst upp till höger på sidan och välj **Min profil**.
1. Klicka **Åtkomsttangenter** på Marketplace-fliken.

   ![magento_products_access_keys_2.4.1.png](/help/troubleshooting/miscellaneous/assets/magento_products_access_keys_2.4.1.png)

1. Klicka **Inaktivera** bredvid åtkomstnyckeln.

## Relaterad läsning

* [Hämta dina autentiseringsnycklar](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/connect-auth.html) i vår dokumentation för utvecklare.
