---
title: 'Distributionen misslyckades vid cachetömning: ''Det finns inga definierade kommandon i namnområdesfelet ''cache'''
description: Den här artikeln innehåller en lösning på problemet när distributionen misslyckas med följande fel **Inga kommandon har definierats i cache-namnutrymmet**.
feature: Deploy
role: Developer
exl-id: ee2bddba-36f7-4aae-87a1-5dbeb80e654e
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---


# Distributionen misslyckades vid cachetömning: &quot;Det finns inga definierade kommandon i namnutrymmesfelet &quot;cache&quot;

>[!WARNING]
>
>Säkerhetskopiera databasen först, om du gör detta på en aktiv produktionsplats, innan du utför dessa steg.

Den här artikeln innehåller en lösning på problemet när distributionen misslyckas och ett av felen i loggen ser ut så här:

```
[YEAR-DAYTIME] ERROR: [127] The command "php ./bin/magento cache:flush --ansi --no-interaction" failed.
        There are no commands defined in the "cache" namespace.
...
      W:     There are no commands defined in the "cache" namespace.
```

## Berörda produkter och versioner

Adobe Commerce i molninfrastruktur 2.4.x

## Problem

<u>Steg som ska återskapas</u>:

Försök att distribuera.

<u>Förväntade resultat</u>:

Du har distribuerats.

<u>Faktiska resultat</u>:

Distributionen misslyckades. I loggarna visas ett distributionsfel med ett meddelande som liknar följande *Det finns inga kommandon i cache-namnområdet*.

### Orsak

Tabellen **`core_config_data`** innehåller konfigurationer för ett lagrings-ID eller webbplats-ID som inte längre finns i databasen. Detta inträffar när du har importerat en databassäkerhetskopia från en annan instans/miljö, och konfigurationerna för dessa omfattningar finns kvar i databasen trots att de associerade arkiven/webbplatserna har tagits bort.

### Lösning

Om du bara har haft en webbplats gäller inte det andra testet för webbplatserna och du behöver bara testa för butiker.

Identifiera de ogiltiga raderna som återstår från konfigurationerna för att lösa problemet.

1. SSH till servern och kör det här kommandot:

   `bin/magento`

1. Felmeddelandet kan visa vilka rader och tabeller som finns kvar i databasen från borttagna platser. Följande är till exempel ett fel som anger att det inte gick att hitta det begärda arkivet:

   ```...
   In StoreRepository.php line 112:
   
   The store that was requested wasn't found. Verify the store and try again.
   ```

1. Kör den här [!DNL MySQL]-frågan för att verifiera att arkivet inte kan hittas, vilket visas i felmeddelandet i steg 2.

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Kör följande [!DNL MySQL]-sats för att ta bort de ogiltiga raderna:

   ```sql
   delete from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Kör det här kommandot igen:

   `bin/magento`

   Om du får ett fel som det nedan som anger att webbplatsen med ID X som begärdes inte hittades har du konfigurationer kvar        i databasen från webbplatser och butiker som har tagits bort.

   ```
   In WebsiteRepository.php line 110:
   
   The website with id X that was requested wasn't found. Verify the website and try again.
   ```

   Kör den här [!DNL MySQL]-frågan och verifiera att webbplatsen inte kan hittas:

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Kör den här [!DNL MySQL]-satsen för att ta bort ogiltiga rader från webbplatskonfigurationen:

   ```sql
   delete from core_config_data where scope='websites' and scope_id not in (select website_id from store_website);
   ```

Kör kommandot `bin/magento` igen för att bekräfta att lösningen fungerade. Felen bör inte längre visas och kan distribueras.

## Relaterad läsning

* [Adobe Commerce felsökare för distribution](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter)
* [Kontrollerar distributionsloggen om molnanvändargränssnittet har felet&quot;loggad&quot;](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error)
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
