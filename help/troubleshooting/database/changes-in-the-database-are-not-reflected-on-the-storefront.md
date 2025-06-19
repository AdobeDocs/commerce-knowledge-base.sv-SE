---
title: Ändringar i databasen återspeglas inte i butiken
description: Den här artikeln innehåller lösningar för att undvika fördröjningar eller avbrott i enhetsuppdateringar. Detta inkluderar hur du undviker att ändra loggtabeller från att bli för stora och hur du ställer in  [!DNL MySQL] tabellutlösare.
exl-id: ac52c808-299f-4d08-902f-f87db1fa7ca6
feature: Catalog Management, Categories, Services, Storefront
role: Developer
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# Ändringar i databasen återspeglas inte i butiken

Den här artikeln innehåller lösningar för att undvika fördröjningar eller avbrott i enhetsuppdateringar. Detta inkluderar hur du undviker att ändra loggtabeller från att bli för stora och hur du konfigurerar [!DNL MySQL] tabellutlösare.

Berörda produkter och versioner:

* Adobe Commerce om molninfrastruktur 2.2.x, 2.3.x
* Adobe Commerce lokal 2.2.x, 2.3.x

## Problem

Ändringar som du gör i databasen visas inte i butiken, eller så är det en avsevärd fördröjning i tillämpningen av entitetsuppdateringar. De enheter som kan påverkas är produkter, kategorier, priser, lager, katalogregler, försäljningsregler och målregler.

## Orsak

Om indexerarna är [konfigurerade att uppdateras av schema](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers) kan problemet bero på en eller flera tabeller där ändringsloggarna är för stora eller att MySQL-utlösare inte har konfigurerats.

### Stora ändringsloggtabeller

Registren för ändringsloggar blir så stora om cron-jobbet `indexer_update_all_views` inte slutförs flera gånger.

Ändringsloggtabeller är de databastabeller där ändringar av enheter spåras. En post lagras i en ändringsloggtabell så länge ändringen inte tillämpas, vilket utförs av kron-jobbet `indexer_update_all_views`. Det finns flera ändringsloggtabeller i en Adobe Commerce-databas, de namnges enligt följande mönster: INDEXER\_TABLE\_NAME + &#39;\_cl&#39;, till exempel `catalog_category_product_cl`, `catalog_product_category_cl`. Mer information om hur ändringar spåras i databasen finns i artikeln [Indexeringsöversikt > Mview](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) i utvecklardokumentationen.

### [!DNL MySQL] databasutlösare har inte konfigurerats

Du misstänker att databasutlösare inte konfigureras om inga poster läggs till i motsvarande ändringsloggtabell efter att en entitet (produkt, kategori, målregel och så vidare) har lagts till eller ändrats.

## Lösning

>[!WARNING]
>
>Vi rekommenderar starkt att du skapar en säkerhetskopia av databasen innan du utför några ändringar och undviker dem under stora belastningsperioder.

### Undvik att ändra loggtabeller som är stora

Kontrollera att seriejobbet `indexer_update_all_views` alltid har slutförts.

Du kan använda följande SQL-fråga för att hämta alla misslyckade instanser av cron-jobbet `indexer_update_all_views`:

```sql
select * from cron_schedule where job_code = "indexer_update_all_views" and status
  <> "success" and status <> "pending";
```

Du kan också kontrollera dess status i loggarna genom att söka efter `indexer_update_all_views`-posterna:

* `<install_directory>/var/log/cron.log` - för version 2.3.1+ och 2.2.8+
* `<install_directory>/var/log/system.log` - för tidigare versioner

### Återställer [!DNL MySQL] tabellutlösare

Om du vill ställa in de saknade [!DNL MySQL] tabellutlösarna måste du ställa in indexeringsläget igen:

1. Växla till Vid sparande.
1. Växla tillbaka till Vid schema.

Använd följande kommando för att utföra den här åtgärden.

>[!WARNING]
>
>Innan du byter indexeringsläge rekommenderar vi att du sätter din webbplats i [underhållsläge](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html?lang=sv-SE#maintenance-mode) och [inaktiverar cron-jobb](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=sv-SE#disable-cron-jobs) för att undvika databaslås.

```bash
php bin/magento indexer:set-mode {realtime|schedule} [indexerName]
```

>[!INFO]
>
>De indexerarrelaterade databasutlösarna läggs till när indexeringsläget är inställt på att schemalägga och tas bort när indexeringsläget är inställt på realtid. Om utlösarna saknas i databasen när indexerarna är inställda på att schemalägga, ändrar du indexerarna till realtid och ändrar dem sedan tillbaka till schemat. Detta återställer utlösarna.

## Relaterad läsning

* [[!DNL MySQL] tabeller är för stora](https://experienceleague.adobe.com/sv/docs/experience-cloud-kcs/kbarticles/ka-26945) i vår kunskapsbas för support
* [Indexering: [!DNL Mview]](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) i utvecklardokumentationen
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
