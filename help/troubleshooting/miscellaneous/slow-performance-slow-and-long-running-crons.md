---
title: Långsamma prestanda, långsamma och långvariga kroner
description: I den här artikeln beskrivs hur du löser problem med webbplatsprestanda och tar lång tid att köra och stoppa kroner som orsakas av att platta tabeller och indexerare har aktiverats.
exl-id: a78ca3c3-85b4-40a1-a693-4703dd3ef4b5
feature: Best Practices, Cache, Categories, Catalog Management
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Långsamma prestanda, långsamma och långvariga kroner

>[!WARNING]
>
>I alla Adobe Commerce-versioner, eftersom vissa tillägg bara fungerar med platta tabeller, finns det en risk om du inaktiverar platta tabeller. Om du vet att du har tillägg som använder platta katalogindexerare kan du behöva ta hänsyn till det när du anger värdena till *Nej*.

I den här artikeln beskrivs hur du löser problem med webbplatsprestanda och kör långsamt och fastnålade cron som orsakas av att [platta tabeller och indexerare](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/catalog-flat) har aktiverats.

BERÖRDA PRODUKTER OCH VERSIONER

* Adobe Commerce i molninfrastruktur 2.1.x och högre
* Adobe Commerce lokal 2.1.x och senare
* Magento Open Source 2.1.x och senare

## Problem

Platta indexerare kan orsaka:

* Omfattande problem med SQL-belastning och platsprestanda.
* Länge löpta och fastnade kroner.

## Orsak

Platta tabeller och indexerare är aktiverade.

## Lösning {#solution}

Från och med Adobe Commerce och Magento Open Source 2.1.x och senare är det inte längre bra att använda en plan katalog, och du rekommenderas inte. Fortsatt användning av den här funktionen är känd för att orsaka prestandaförsämring och andra indexeringsproblem. Så här inaktiverar du den platta katalogen:

1. Gå till **Lagrar** > **Inställningar** > **Konfiguration** i Admin.
1. Välj **Katalog** på panelen till vänster under **Katalog** .
1. Expandera avsnittet **Storefront** och gör följande:
   * Ange **Använd platt katalogkategori** till *Nej*.
   * Ange **Använd platt katalogprodukt** till *Nej*.
1. Klicka på **Spara konfiguration** när du är klar. Uppdatera sedan cacheminnet när du uppmanas till detta.
1. Rensa cachen genom att köra `php bin/magento cache:flush`.

Om du inte kan ändra **Använd platt katalog** och **Använd platt katalog** till *Nej* eftersom alternativen är nedtonade kan du inaktivera platta indexerare i `app/etc/config.php`:

1. Kör det här kommandot för att se till att alla indexerare är inställda på Uppdatera enligt schema: `php bin/magento indexer:set-mode schedule`.
1. Redigera `app/etc/config.php` och leta upp raderna med `flat_catalog_product` och `flat_catalog_category` - ändra dem från 1 till 0 för att inaktivera dem.
1. Kör kommandot `php bin/magento app:config:import`
1. Kör det här kommandot för att bekräfta att platta indexerare är inaktiverade: `php        bin/magento indexer:status`.
1. Rensa cachen genom att köra `php bin/magento cache:flush`.

## Relaterad information

[Återställ Adobe Commerce cron-jobb som fastnat manuellt i molnet](/help/how-to/general/reset-stuck-magento-cron-jobs-manually-on-cloud.md) i vår kunskapsbas för support.
