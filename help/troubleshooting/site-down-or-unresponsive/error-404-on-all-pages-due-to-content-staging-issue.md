---
title: Fel 404 på alla sidor på grund av problem med Content Staging
description: I den här artikeln finns en fix för Adobe Commerce lokalt och Adobe Commerce om molninfrastrukturproblem där du får ett 404-fel när du öppnar en butikssida eller Commerce Admin.
exl-id: 62d8ba6e-8550-4e1e-8e8d-8f319c92778a
feature: CMS, Catalog Management, Categories, Page Content, Staging
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# Fel 404 på alla sidor på grund av problem med Content Staging

I den här artikeln finns en fix för Adobe Commerce lokalt och Adobe Commerce om molninfrastrukturproblem där du får ett 404-fel när du öppnar en butikssida eller Commerce Admin.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.2.x, 2.3.x
* Adobe Commerce om molninfrastruktur 2.2.x, 2.3.x

## Problem

>[!NOTE]
>
>Den här artikeln gäller inte den situation där du får ett 404-fel när du försöker [förhandsgranska mellanlagringsuppdateringen](https://docs.magento.com/user-guide/cms/content-staging-scheduled-update.html#preview-the-scheduled-change). Om du stöter på ett sådant problem, öppna ett [supportbiljett](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

Om du får åtkomst till en butikssida eller Admin genereras felet 404 (sidan&quot;Hopp, vår dåliga...&quot;) efter att du har utfört åtgärder med schemalagda uppdateringar för att lagra innehåll med hjälp av [Innehållsmellanlagring](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) (uppdateringar av butiksinnehållsresurser som schemaläggs med [Magento\_Mellanlagringsmodul](https://developer.adobe.com/commerce/php/module-reference/)). Du kan till exempel ha tagit bort en produkt med en schemalagd uppdatering eller tagit bort slutdatumet för den schemalagda uppdateringen.

En resurs för butiksinnehåll innehåller:

* Produkt
* Kategori
* Katalogprisregel
* Kundprisregel
* CMS-sida
* CMS-block
* Widget

Vissa scenarier beskrivs i avsnittet Orsak nedan.

## Orsak

The `flag` tabellen i databasen (DB) innehåller ogiltiga länkar till `staging_update` tabell.

Problemet är relaterat till innehållsindelning. Nedan visas två olika scenarier. Observera att det kan finnas fler situationer som utlöser problemet.

**Scenario 1** Tar bort en resurs för butiksinnehåll som:

* har en uppdatering schemalagd med Content Staging
* uppdateringen har ett slutdatum (vilket innebär det förfallodatum efter vilket den uppdaterade tillgången återgår till sin tidigare version)
* uppdateringens slutdatum har passerat

Samtidigt kan problemet bero på att en borttagen tillgång inte har något slutdatum för den schemalagda uppdateringen.

**Scenario 2** Tar bort slutdatumet/sluttiden för en schemalagd uppdatering.

### Identifiera om ditt problem är relaterat

Kör följande DB-fråga för att identifiera om problemet som du har drabbats av är det som beskrivs i den här artikeln:

```sql
   SELECT f.flag_data >'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists
   -> FROM flag f
   -> LEFT JOIN staging_update su
   -> ON su.id = f.flag_data >'$.current_version'
   -> WHERE flag_code = 'staging';
```

Om frågan returnerar en tabell där `update_exists` värdet är &quot;0&quot;, så en ogiltig länk till `staging_update` tabellen finns i databasen och stegen som beskrivs i [Lösningsavsnitt](#solution) hjälper till att lösa problemet. Följande är ett exempel på frågeresultatet med `update_exists` värdet är lika med &quot;0&quot;:

![update_exists_0.png](assets/update_exists_0.png)

Om frågan returnerar en tabell där `update_exists` värdet är &quot;1&quot; eller ett tomt resultat, vilket betyder att ditt problem inte är relaterat till mellanlagringsuppdateringar. Följande är ett exempel på frågeresultatet med `update_exists` värde lika med &quot;1&quot;:

![updates_exist_1.png](assets/updates_exist_1.png)

I det här fallet kan du hänvisa till [Felsökare för nedtryckt webbplats](/help/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.md) för felsökning av idéer.

## Lösning

1. Kör följande fråga för att ta bort den ogiltiga länken till `staging_update` tabell:

   ```sql
   DELETE FROM flag WHERE flag_code = 'staging';
   ```

1. Vänta tills cron-jobbet körs (körs på upp till fem minuter om konfigurationen är korrekt) eller kör det manuellt om du inte har ställt in cron.

Problemet bör lösas direkt efter att den ogiltiga länken har åtgärdats. Om problemet kvarstår [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
