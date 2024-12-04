---
title: CSV-filen för exporterade produkter visas inte
description: I den här artikeln finns en korrigering av problemet där du försöker exportera den önskade entitetstypen till en CSV-fil i Commerce Admin, men filen visas inte.
exl-id: 8e3bb65c-ea75-4af4-ad4b-4d94ab219bbb
feature: Cache, Data Import/Export, Products, Variables
role: Developer
source-git-commit: b6f1222918b027eaecda42b767e6f83b2cf0f5d0
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 0%

---

# CSV-filen för exporterade produkter visas inte

I den här artikeln finns en lösning på problemet där export av önskad entitetstyp till en CSV-fil i Commerce Admin resulterar i att filen inte visas.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen, alla [versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problem

<u>Steg som ska återskapas</u>

Krav: Alternativet **Lägg till hemlig nyckel till URL:er** är inställt på *Ja*. Alternativet är konfigurerat i Commerce Admin under **Lagrar** > **Konfiguration** > **Avancerat** > **Admin** > **Säkerhet**.

1. Gå till **System** > **Dataöverföring** > **Exportera** i Admin.

   ![magento_export_products_2.3.4.png](assets/magento_export_products_2.3.4.png)

1. Välj
   * **Entitetstyp**: Den entitet du vill exportera
   * **Exportera filformat**: *CSV*
   * **Fältbilaga**: lämna omarkerat.
1. Klicka på **Fortsätt**.
1. Följande meddelande visas: *&quot;Meddelande läggs till i kö, väntar på att hämta filen snart&quot;*.

<u>Förväntat resultat</u>

CSV-filen som innehåller den exporterade önskade entitetstypen visas i rutnätet inom några minuter.

<u>Faktiskt resultat</u>

CSV-filen som innehåller den exporterade önskade entitetstypen visas inte i rutnätet på 10 minuter eller mer.

## Orsak

Ett känt fel med exportfunktionen i Adobe Commerce programdel version 2.3.2.

## Lösning

Det finns två möjliga lösningar på problemet:

* Inaktivera alternativet Lägg till hemlig nyckel till URL.
* Kör kommandot `bin/magento queue:consumers:start exportProcessor` manuellt och konfigurera det som ska köras av cron om du vill.

Mer information om båda alternativen finns i följande stycken.

### Inaktivera alternativet Lägg till hemlig nyckel till URL

1. Gå till **Lagrar** > **Konfiguration** > **Avancerat** > **Admin** > **Säkerhet** i Admin.
1. Ange alternativet **Lägg till hemlig nyckel till URL:er** till *Nej*
1. Klicka på **Spara konfiguration**.
1. Rensa cache under **System** > **Verktyg** > **Cachehantering** eller genom att köra    ```bash    bin/magento cache:clean``` eller i Admin.

### Kör exportkommandot manuellt och lägg till det som cron-jobb

Om du vill hämta exportfilen kör du kommandot `bin/magento queue:consumers:start exportProcessor`. När du har kört detta bör filen visas i rutnätet.


Om du vill lägga till processen som ett cron-jobb måste du lägga till variabeln `CRON_CONSUMERS` i filen `.magento.env.yaml`.

#### Lägg till process som ett cron-jobb (valfritt)

1. Se till att kranen är konfigurerad och konfigurerad. Mer information finns i [Konfigurera cron-jobb](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html).
1. Kör följande kommando om du vill returnera en lista över användare av meddelandekön:     `./bin/magento queue:consumers:list`
1. Lägg till följande i din `.magento.env.yaml`-fil i rotprogramkatalogen och inkludera de konsumenter som du vill lägga till. Här är till exempel den konsument som krävs för exportbearbetning:

   ```yaml
   stage:
       deploy:
           CRON_CONSUMERS_RUNNER:
               cron_run: true
               max_messages: 1000
               consumers:
                   - exportProcessor
   ```

   Tryck sedan på den här uppdaterade filen och distribuera om miljön. Referera även till [Lägg till anpassade cron-jobb i ditt projekt](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#add-custom-cron-jobs-to-your-project) i utvecklardokumentationen.

>[!NOTE]
>
>Om du inte kan hitta filen `.magento.env.yaml` för din miljö, och du tror att den har tagits bort, måste du skapa en ny `.magento.env.yaml`. Det kan vara tomt från början, du kan lägga till information där efter behov. Referera till följande artiklar: [Konfigurera miljövariabler för distribution](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) och [miljövariabler](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) i vår utvecklardokumentation.

>[!TIP]
>
>[YAML-filer](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) är skiftlägeskänsliga och tillåter inte tabbar. Var noga med att använda konsekvent indrag i hela .magento.env.yaml-filen, annars kanske inte konfigurationen fungerar som förväntat. Exemplen i dokumentationen och i exempelfilen använder indrag med två mellanslag. Kontrollera konfigurationen med hjälp av kommandot validate för verktygen.

>[!NOTE]
>
>I Adobe Commerce-projekt för molninfrastruktur på Pro måste funktionen [för automatiska kroner](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=en#crontab) vara aktiverad i din Adobe Commerce i molninfrastruktur innan du kan lägga till anpassade kron-jobb i miljöer för förproduktion och produktion med `.magento.app.yaml`. Om den här funktionen inte är aktiverad kan du [skapa en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) och lägga till jobbet åt dig.
