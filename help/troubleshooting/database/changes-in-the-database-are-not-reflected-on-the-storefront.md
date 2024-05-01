---
title: Ändringar i databasen återspeglas inte i butiken
description: Den här artikeln innehåller lösningar för att undvika fördröjningar eller avbrott i enhetsuppdateringar. Detta inkluderar hur du undviker att ändra loggtabeller från att bli för stora och hur du konfigurerar MySQL-tabellutlösare.
exl-id: ac52c808-299f-4d08-902f-f87db1fa7ca6
feature: Catalog Management, Categories, Services, Storefront
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# Ändringar i databasen återspeglas inte i butiken

Den här artikeln innehåller lösningar för att undvika fördröjningar eller avbrott i enhetsuppdateringar. Detta inkluderar hur du undviker att ändra loggtabeller från att bli för stora och hur du konfigurerar MySQL-tabellutlösare.

Berörda produkter och versioner:

* Adobe Commerce om molninfrastruktur 2.2.x, 2.3.x
* Adobe Commerce lokal 2.2.x, 2.3.x

## Problem

Ändringar som du gör i databasen visas inte i butiken, eller så är det en avsevärd fördröjning i tillämpningen av entitetsuppdateringar. De enheter som kan påverkas är produkter, kategorier, priser, lager, katalogregler, försäljningsregler och målregler.

## Orsak

Om indexerarna [konfigurerad att uppdatera enligt schema](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html#configure-indexers)kan problemet bero på en eller flera tabeller där ändringsloggarna är för stora eller där MySQL-utlösare inte har konfigurerats.

### Stora ändringsloggtabeller

Ändringsloggtabellerna blir så stora om `indexer_update_all_views` cron-jobbet har inte slutförts flera gånger.

Ändringsloggtabeller är de databastabeller där ändringar av enheter spåras. En post lagras i en ändringsloggtabell så länge ändringen inte tillämpas, vilket utförs av `indexer_update_all_views` cron-jobb. Det finns flera ändringsloggtabeller i en Adobe Commerce-databas, de namnges enligt följande mönster: INDEXER\_TABLE\_NAME + ‘\_cl’, till exempel `catalog_category_product_cl`, `catalog_product_category_cl`. Du hittar mer information om hur ändringar spåras i databasen i [Indexeringsöversikt > Mview](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#m2devgde-mview) artikel i vår dokumentation för utvecklare.

### Utlösare för MySQL-databas har inte konfigurerats

Du misstänker att databasutlösare inte konfigureras om inga poster läggs till i motsvarande ändringsloggtabell efter att en entitet (produkt, kategori, målregel och så vidare) har lagts till eller ändrats.

## Lösning

>[!WARNING]
>
>Vi rekommenderar starkt att du skapar en säkerhetskopia av databasen innan du utför några ändringar och undviker dem under stora belastningsperioder.

### Undvik att ändra loggtabeller som är stora

Se till att `indexer_update_all_views` cron-jobbet har alltid slutförts.

Du kan använda följande SQL-fråga för att hämta alla misslyckade instanser av `indexer_update_all_views` cron-jobb:

```sql
select * from cron_schedule where job_code = "indexer_update_all_views" and status
  <> "success" and status <> "pending";
```

Du kan också kontrollera dess status i loggarna genom att söka efter `indexer_update_all_views` poster:

* `<install_directory>/var/log/cron.log` - för version 2.3.1+ och 2.2.8+
* `<install_directory>/var/log/system.log` - för tidigare versioner

### Ange MySQL-tabellutlösare igen

Om du vill ställa in de saknade MySQL-tabellutlösarna måste du ställa in indexeringsläget igen:

1. Växla till Vid sparande.
1. Växla tillbaka till Vid schema.

Använd följande kommando för att utföra den här åtgärden.

>[!WARNING]
>
>Innan du byter indexeringsläge rekommenderar vi att du använder [underhåll](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode) läge och [inaktivera cron-jobb](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs) för att undvika databaslås.

```bash
php bin/magento indexer:set-mode {realtime|schedule} [indexerName]
```

>[!INFO]
>
>De indexerarrelaterade databasutlösarna läggs till när indexeringsläget är inställt på att schemalägga och tas bort när indexeringsläget är inställt på realtid. Om utlösarna saknas i databasen när indexerarna är inställda på att schemalägga, ändrar du indexerarna till realtid och ändrar dem sedan tillbaka till schemat. Detta återställer utlösarna.

## Relaterad läsning

<ul><li title="MySQL-tabeller är för stora"><a href="/help/troubleshooting/database/mysql-tables-are-too-large.md">MySQL-tabeller är för stora</a> i vår kunskapsbas för support.</li>
<li title="MySQL-tabeller är för stora"><a href="https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#m2devgde-mview">Översikt över indexeraren &gt; Mview</a> i vår dokumentation för utvecklare.</li></ul>
