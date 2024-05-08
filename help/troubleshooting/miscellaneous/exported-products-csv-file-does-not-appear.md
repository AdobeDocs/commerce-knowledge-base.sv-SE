---
title: CSV-filen för exporterade produkter visas inte
description: I den här artikeln finns en lösning på problemet där du försöker exportera produkter till en CSV-fil i Commerce Admin, men filen visas inte.
exl-id: 8e3bb65c-ea75-4af4-ad4b-4d94ab219bbb
feature: Cache, Data Import/Export, Products, Variables
role: Developer
source-git-commit: d55702ab97f3770d0ec71322f6c24448f0169ad4
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# CSV-filen för exporterade produkter visas inte

I den här artikeln finns en lösning på problemet där du försöker exportera produkter till en CSV-fil i Commerce Admin, men filen visas inte.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen, alla [versionerna](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problem

<u>Steg som ska återskapas</u>

Krav: **Lägg till hemlig nyckel till URL:er** option is set to *Ja*. Alternativet är konfigurerat i Commerce Admin under **Lager** > **Konfiguration** > **Avancerat** > **Administratör** > **Säkerhet**.

1. Gå till Admin **System** > **Dataöverföring** > **Exportera**.

   ![magento_export_products_2.3.4.png](assets/magento_export_products_2.3.4.png)

1. Välj
   * **Enhetstyp**: *Produkter*
   * **Exportera filformat**: *CSV*
   * **Fälthölje**: lämna omarkerat.
1. Klicka **Fortsätt**.
1. Följande meddelande visas: *&quot;Meddelande läggs till i kö, vänta på att få filen snart&quot;*.

<u>Förväntat resultat</u>

CSV-filen med de exporterade produkterna visas i rutnätet om några minuter.

<u>Faktiskt resultat</u>

CSV-filen med de exporterade produkterna visas inte i rutnätet på 10 minuter eller mer.

## Orsak

Ett känt fel med exportfunktionen i Adobe Commerce programdel version 2.3.2.

## Lösning

Det finns två möjliga lösningar på problemet:

* Inaktivera alternativet Lägg till hemlig nyckel till URL.
* Kör `bin/magento queue:consumers:start exportProcessor` manuellt och konfigurera det som ska köras av cron om du vill.

Mer information om båda alternativen finns i följande stycken.

### Inaktivera alternativet Lägg till hemlig nyckel till URL

1. Gå till Admin **Lager** > **Konfiguration** > **Avancerat** > **Administratör** > **Säkerhet**.
1. Ange **Lägg till hemlig nyckel till URL:er** alternativ till *Nej.*
1. Klicka **Spara konfiguration**.
1. Rensa cacheminne under **System** > **verktyg** > **Cachehantering** eller genom att köra    ```bash    bin/magento cache:clean``` eller i Admin.

### Kör exportkommandot manuellt och lägg till det som cron-jobb

Om du vill hämta exportfilen kör du `bin/magento queue:consumers:start exportProcessor` -kommando. När du har kört detta bör filen visas i rutnätet.


Om du vill lägga till processen som ett cron-jobb måste du lägga till `CRON_CONSUMERS` variabeln till `.magento.env.yaml` -fil.

#### Lägg till process som ett cron-jobb (valfritt)

1. Se till att kranen är konfigurerad och konfigurerad. Se [Ställ in cron-jobb](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) för mer information.
1. Kör följande kommando om du vill returnera en lista över användare av meddelandekön:     `./bin/magento queue:consumers:list`
1. Lägg till följande i `.magento.env.yaml` i programmets rotkatalog och inkludera de konsumenter som du vill lägga till. Här är till exempel den konsument som krävs för exportbearbetning:

   ```yaml
   stage:
       deploy:
           CRON_CONSUMERS_RUNNER:
               cron_run: true
               max_messages: 1000
               consumers:
                   - exportProcessor
   ```

   Tryck sedan på den här uppdaterade filen och distribuera om miljön. Även referens [Lägg till anpassade cron-jobb i ditt projekt](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#add-custom-cron-jobs-to-your-project) i vår dokumentation för utvecklare.

>[!NOTE]
>
>Om du inte hittar `.magento.env.yaml` för din miljö, och du tror att den har tagits bort, måste du skapa en ny `.magento.env.yaml`. Det kan vara tomt från början, du kan lägga till information där efter behov. Referera till följande artiklar: [Konfigurera miljövariabler för distribution](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) och [Miljövariabler](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) i vår dokumentation för utvecklare.

>[!TIP]
>
>[YAML-filer](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) är skiftlägeskänsliga och tillåter inte tabbar. Var noga med att använda konsekvent indrag i hela .magento.env.yaml-filen, annars kanske inte konfigurationen fungerar som förväntat. Exemplen i dokumentationen och i exempelfilen använder indrag med två mellanslag. Kontrollera konfigurationen med hjälp av kommandot validate för verktygen.

>[!NOTE]
>
>På Adobe Commerce i Cloud Infrastructure Pro-projekt [funktionen för automatiska kroner](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=en#crontab) måste aktiveras på din Adobe Commerce i molninfrastruktur innan du kan lägga till anpassade cron-jobb i förings- och produktionsmiljöer med `.magento.app.yaml`. Om funktionen inte är aktiverad [skapa en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), så att jobbet läggs till åt dig.
