---
title: Distributionsfel vid implementering av felaktiga filer
description: Den här artikeln innehåller en lösning för problemet när du får distributionsfel som orsakas av felaktiga implementeringar i databasen med filer/mappar som inte borde ha lagts till.
feature: Deploy
role: Developer
exl-id: c795f9d5-7171-4846-b99f-c018f1d2bf12
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Distributionsfel vid implementering av felaktiga filer

Den här artikeln innehåller en korrigering för problemet när du får distributionsfel som orsakas av felaktiga implementeringar i databasen med filer/mappar som inte borde ha lagts till.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur (alla versioner)

## Problem

Distributionsfel uppstår när du implementerar i databasen med filer/mappar. Följande fel orsakas till exempel av ett försök att ansluta till databasen när den inte är tillgänglig under [byggfasen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?lang=sv-SE#build-phase):

```SQL
SQLSTATE[HY000] [2002] php_network_getaddresses: getaddrinfo for database.i  
          nternal failed: Name or service not known                                    
                                                                                       
        
        In Abstract.php line 124:
                                                                                       
          SQLSTATE[HY000] [2002] php_network_getaddresses: getaddrinfo for database.i  
          nternal failed: Name or service not known                                    
                                                                                       
        
        In Abstract.php line 124:
                                                                                       
          PDO::__construct(): php_network_getaddresses: getaddrinfo for database.inte  
          rnal failed: Name or service not known       
```

## Orsak

Vissa filer/mappar bör inte implementeras i databasen eftersom de orsakar en brytning i [distributionsarbetsflödet](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?lang=sv-SE).

## Lösning

Ta bort dessa filer/mappar från databasen om de finns:

* `app/etc/env.php`
* `pub/media/catalog`
* `vendor`
