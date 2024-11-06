---
title: Felmeddelande när webbplatser läggs till i säkerhetsgenomsökningen
description: Den här artikeln innehåller möjliga lösningar på problemet när en användare inte kan lägga till webbplatser i [Commerce Security Scan](https://account.magento.com/scanner/dashboard/).
exl-id: 8d000ca4-b977-432d-bb26-6ea320067a40
feature: Cache, Compliance, Console, Security
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Felmeddelande när webbplatser läggs till i säkerhetsgenomsökningen

Den här artikeln innehåller möjliga lösningar på problemet när en användare inte kan lägga till webbplatser i [Commerce Security Scan](https://account.magento.com/scanner/dashboard/).

## Berörda produkter och versioner

* Adobe Commerce (alla distributionsmetoder och versioner)
* Magento Open Source

## Problem

Användaren kan inte lägga till webbplatser i [Commerce Security Scan](https://account.magento.com/scanner/dashboard/). Följande felmeddelande visas när du försöker lägga till en plats: *Det går inte att skicka webbplatsen för skanning.*

## Lösning

1. Kontrollera att följande IP-adresser inte blockeras på portarna 80 och 443:
   * 52.87.98.44
   * 34.196.167.176
   * 3.218.25.102

1. Bekräftelsekoden är tidskänslig. Om mer än 30 minuter har gått sedan länken **Lägg till plats** klickades har koden förmodligen gått ut.
1. Glöm inte att rensa cacheminnet och kontrollera att valideringskoden visas i källtexten för startsidan. Bekräftelsekoden ska injiceras enligt HTML markup specs: HTML-kommentaren kan injiceras i sidbrödtexten (vi föreslår att den placeras i sidfotsavsnittet); META-taggen ska endast finnas i head-avsnittet.
1. Innan du klickar på **Verifiera bekräftelsekod** öppnar du webbläsarens utvecklarkonsol, klickar på fliken **Nätverk** och kontrollerar svaret från magento.com. Det ska vara HTTP 200 (OK) och svarstexten ska innehålla ett JSON-objekt.
1. Om svarskoden är HTTP 200 och svarstexten är ett JSON-objekt och egenskapsvärdet `verified` är `false` betyder det att koden inte hittas på sidan. Egenskapsvärdet `details` ska innehålla förklaringen. Om arkivet till exempel använder ett självsignerat SSL-certifikat kommer det antagligen att finnas ett anslutningsfel.

Om du fortfarande inte kan lägga till webbplatser utför du följande steg:

1. Placera ytterligare en HTML-kommentar på sidan:

   ```HTML
   <!-- MAGEID:Your magento.com ID, EMAIL:your email address -->
   ```

1. Skicka in en supportanmälan och lämna följande information:
   * Adobe Commerce store URL
   * MAGEID + Magento.com
   * Förnamn + Efternamn
   * Företag
   * E-postlista för kommaseparerade meddelanden

## Relaterad läsning

* [Säkerhetsgenomsökning](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) i vår användarhandbok.
