---
title: 'MDVA-11189: catalogLayout_stock rows deleted post CSV import'
description: MDVA-11189 Adobe Commerce-korrigeringen åtgärdar problemet när en CSV-fil för uppdatering av produktlager har importerats och rader från tabellen "cataloglager_stock" tas bort. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 är installerat. Patch-ID:t är MDVA-1189. Observera att problemet har åtgärdats i Adobe Commerce 2.3.5.
exl-id: 84e1979c-826c-4c01-b0c7-8054bb4b23f0
feature: Catalog Management, Data Import/Export, Inventory, Orders
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# MDVA-11189: catalogLayout_stock rows removed post CSV import

MDVA-11189 Adobe Commerce-korrigeringen åtgärdar problemet när rader i tabellen `cataloginventory_stock` tas bort efter att en CSV-fil har importerats för att uppdatera produktarkivet. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 är installerat. Patch-ID:t är MDVA-1189. Observera att problemet har åtgärdats i Adobe Commerce 2.3.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-version:** Adobe Commerce i molninfrastruktur 2.2.3

**Kompatibel med Adobe Commerce-versioner:** Adobe Commerce (alla distributionsmetoder) 2.3.0-2.3.4-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Åtgärdar problemet när rader i tabellen `cataloginventory_stock` tas bort efter att en `.csv` har importerats för att uppdatera produktlager.

<u>Steg att återskapa:</u>

1. Kör följande MySQL-kommando i databasen: `select count(*) from cataloginventory_stock_status;`
1. Notera antalet rader.
1. Ange crontab enligt följande: `* * * * * /usr/bin/php <path to installation>/bin/magento cron:run  | grep -v "Ran jobs by schedule" >> <path to installation>/var/log/cron.log 2>&1`
1. Gå till panelen Admin i **System** > **Verktyg** > **Indexhantering**.
1. Ställ in indexerare på *Uppdatera efter schema.*
1. Gå till **System** > *Dataöverföring* > **Exportera**.
1. Ange **entitetstypen** som lika med *Produkter* > **Fortsätt**.
1. Öppna den sparade `.csv`-filen > Ta bort alla kolumner utom SKU och QTY.
1. Uppdatera kvantiteten för alla produkter till 150.
1. Spara filen `.csv`.
1. Gå till **System** > *Dataöverföring* > **Importera** .
1. Ange följande värden:
   1. Entitetstyp: *Produkter*
   1. Importbeteende: *Lägg till/uppdatera*
   1. Låt alla andra värden vara som standard.
   1. Välj Arkiv för att välja katalogproduktkalkylbladet.
1. Klicka på **Kontrollera data** > **Importera**. Det kan ta 5-10 minuter.
1. Kör följande MySQL-kommando i databasen:
   `select count(*) from cataloginventory_stock_status;`

<u>Faktiskt resultat:</u>

Antalet rader i `cataloginventory_stock` minskas efter CSV-importen för att uppdatera lagret.

<u>Förväntat resultat:</u>

Antalet rader i `cataloginventory_stock` ska vara detsamma efter CSV-importen för att uppdatera lagret.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
