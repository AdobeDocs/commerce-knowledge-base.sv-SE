---
title: Produkten visas inte i butiken
description: Den här artikeln innehåller lösningar för när produkter inte visas i butiken.
exl-id: 454eca5b-4722-46e0-8e5d-3daf8e3e675a
feature: Cache, Categories, Console, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# Produkten visas inte i butiken

Den här artikeln innehåller lösningar för när produkter inte visas i butiken.

## Berörda produkter och versioner

* Adobe Commerce lokal X.X.X
* Adobe Commerce i molninfrastrukturen X.X.X

## Problem

<u>Steg som ska återskapas</u>:

1. Logga in på Commerce Admin.
1. Gå till **Katalog** > **Produkter**.

   ![open_product_page_magento_2.4.1.png](assets/open_product_page_magento_2.4.1.png)

1. Klicka på **Lägg till produkt** och gå igenom produktskapandeprocessen. Eller importera produkter från en CSV-fil.

<u>Förväntat resultat</u>:

Produkten visas i butiken.

<u>Faktiskt resultat</u>:

Produkten visas inte.

## Orsak

Detta kan bero på flera olika orsaker. Följ stegen nedan för att kontrollera de huvudpunkter som kan hjälpa dig att identifiera och lösa problemet.

## Lösning

Var och en av följande punkter kan lösa problemet.

* Kontrollera produktinställningarna i Admin. Gå till **Katalog** > **Produkter**, öppna produktsidan och kontrollera att följande fält är korrekt konfigurerade:
   * **Aktivera produkt** = *Ja.*
   * **Stock-status**: *I Stock*. Eller om *Slut på lager* är rätt värde kontrollerar du att **Visa Utanför Stock-produkter** (**STORES** > **Inställningar** > **Konfiguration** > **KATALOG** > **Lager** > **Stock-alternativ** > **Visa ej i lager**) är inställt på *Ja* (konfigurerat på global nivå).
   * **Kategorier**: Om du försöker hitta produkten på en kategorisida kontrollerar du att produkten är tilldelad kategorin. Om du vill förenkla felsökningen skapar du en ny kategori på den aktuella sidan och tilldelar en produkt till den.
   * **Synlighet** = *Katalog, sökning.*
   * Kontrollera att produkten har tilldelats rätt webbplats i avsnittet **Produkt i webbplatser**.
   * Växla omfångsväljaren till butiksvyn där du försöker hitta produkten i butiken och verifiera samma inställningar.
* Utför den fullständiga omindexeringen genom att köra `bin/magento indexer:reindex` från konsolen och tömma all cache i Admin, under **System** > **Verktyg** > **Cachehantering**, eller från konsolen genom att köra `bin/magento cache:clean`.
* Om ovanstående inte hjälper kan du starta ytterligare undersökningar genom att kontrollera loggar i katalogen `var/log`.

## Relaterad läsning i vår kunskapsbas

* [Loggplatser (kataloger) för Pro-arkitekturen](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md)
* [Loggplatser (kataloger) för Starter-arkitekturen](/help/how-to/general/log-locations-directories-for-starter-plan.md)
