---
title: Distributionen misslyckas med rätt åtkomstnycklar i env:COMPOSER_AUTH eller auth.json
description: Den här artikeln innehåller en lösning på problemet när distributionen misslyckas med följande fel:"https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip gick inte att hämta (HTTP/1.1 404 Hittades inte)".
feature: Deploy
role: Admin
exl-id: a18f4213-7381-4001-a5a0-3f8db4525469
source-git-commit: 54ef4e95cf0e3f5822ff5e5c566129fab331f784
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# Distributionen misslyckas med rätt åtkomstnycklar i env:COMPOSER_AUTH eller auth.json

I den här artikeln finns en lösning på problemet när distributionen misslyckas med ett fel som det nedan, i [distributionslogg](/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log):

```
W:   [Composer\Downloader\TransportException]
W:   The "https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip" file could not be downloaded (HTTP/1.1 404 Not Found)
```

## Berörda produkter och versioner

Adobe Commerce i molninfrastruktur 2.4.x

## Problem  

<u>Steg som ska återskapas</u>:

Försök att distribuera. 

<u>Förväntade resultat</u>:

Du har distribuerats.

<u>Faktiska resultat</u>:

>[!NOTE]
>
>Detta är ett exempelfel. Du kan få ett fel som anger en annan fil (beroende på vilken Adobe Commerce-version du distribuerar).

Distributionen misslyckades. Du ser ett liknande fel *Det gick inte att hämta filen https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip (HTTP/1.1 404 Hittades inte)* i [distributionslogg](/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).


### Orsak

De angivna åtkomstnycklarna för dispositionen som finns på någon av dessa platser kanske inte har åtkomst till koden:

* i `env:COMPOSER_AUTH` variabel på projektnivå
* i `auth.json file`, som har företräde framför `env:COMPOSER_AUTH` variabel.

### Lösning

Uppdatera `env:COMPOSER_AUTH` på projektnivå och se till att den är konfigurerad med nycklar som har åtkomst till koden.

Om du vill se steg går du till [Variabelnivåer](/docs/commerce-cloud-service/user-guide/configure/env/variable-levels) i Commerce om Cloud Infrastructure Guide.

## Relaterad läsning

* [Det gick inte att komma åt Adobe Commerce i molnet: 403 Otillåten eller 404 Inte hittad vid distribution](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html)
* [Distributionsfel: fel 7 vid hämtning ... port 443: Anslutningen nekades](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-error-downloading-connection-refused-adobe-commerce)
