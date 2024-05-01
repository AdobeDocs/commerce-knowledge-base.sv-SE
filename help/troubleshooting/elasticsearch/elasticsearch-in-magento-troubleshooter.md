---
title: Elasticsearch i Adobe Commerce felsökare
description: Problem med Elasticsearch i Adobe Commerce kan lösas med felsökningsverktyget i Elasticsearch. Klicka på varje fråga för att visa svaret i varje steg i felsökaren.
exl-id: acae0da0-2918-4021-9fbe-c138940c5a72
feature: Categories
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 0%

---

# Elasticsearch i Adobe Commerce felsökare

Problem med Elasticsearch i Adobe Commerce kan lösas med felsökningsverktyget i Elasticsearch. Klicka på varje fråga för att visa svaret i varje steg i felsökaren.

>[!WARNING]
>
>Observera att uppgraderingar av tjänster inte kan implementeras i produktionsmiljön utan att vårt infrastrukturteam får 48 arbetstimmar varsel om detta på Adobe Commerce molninfrastruktur. Detta är nödvändigt eftersom vi måste se till att det finns en infrastruktursupporttekniker tillgänglig som kan uppdatera din konfiguration inom en önskad tidsram med minimala driftavbrott i din produktionsmiljö. Så 48 timmar före när ändringarna måste vara i produktion [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) ange vilken serviceuppgradering du behöver och ange när du vill att uppgraderingen ska starta.

## Steg 1 - Sök efter Elasticsearch {#step-1}

+++**Kan ditt problem relatera till Elasticsearch?**

Elasticsearch problem som anges i felmeddelanden, &quot;_Inga aktiva noder hittades i ditt kluster&quot;,_ produkter som saknas och information om gamla produkter.

a. JA - Fortsätt till [Steg 2](#step-2).\
b. NEJ - Sök igen på relevanta söktermer i [Adobe Commerce Help Center Knowledge Base](https://support.magento.com/hc).

+++

## Steg 2 - Sök efter installationsproblem {#step-2}

+++**Är det en ny installation av Elasticsearch?**

a. JA - [Kontrollera att Elasticsearch är korrekt installerat.](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) Kontrollera även om du använder Adobe Commerce i molninfrastruktur 2.3.1 eller senare. Handlare som har uppgraderat till Adobe Commerce i molninfrastruktur (version 2.3.1 och senare) och som använder en tidigare version av Elasticsearch än version 6.x kan råka ut för fel vid distributionen. För att lösa det här problemet måste klientmodulen och tjänsten Elasticsearch finnas på de senaste rekommenderade versionerna av Elasticsearch. För steg se [Elasticsearch problem efter uppgraderingen av Adobe Commerce om molninfrastruktur 2.3.1+](/help/troubleshooting/elasticsearch/elasticsearch-issues-after-magento-commerce-cloud-2-3-1-upgrade.md).\
b. NEJ - Kontrollera klustrets hälsotillstånd. Om du arbetar i en Pro-miljö för staging eller produktion kör du det här kommandot: `curl -m1 localhost:9200/_cluster/health?pretty`. Kör om du arbetar i en integreringsmiljö (som innehåller alla startgrenar) `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty`. Fortsätt till [Steg 3](#step-3).

+++

## Steg 3 - Kontrollera om Elasticsearch-klustret är tillgängligt {#step-3}

+++**Fick du ett servicesvar?**

a. JA - Fortsätt till [Steg 4](#step-4).\
b. NEJ - Fortsätt till [Steg 9](#step-9).

+++

## Steg 4 - Verifiera att Elasticsearch-klustret är felfritt {#step-4}

+++**Response green?**

a. JA - Elasticsearch finns för databehandling och omindexering bör fungera. Fortsätt till [Steg 5](#step-5).\
b. NO - Gul eller röd betyder att det finns problem med anslutningar mellan noder, och vissa data kanske inte är tillgängliga. Kör kommandot om det är gult: `php bin/magento config:show catalog/search/engine` för att kontrollera sökmotorn. Fortsätt till [Steg 6](#step-6). Om rött, [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Steg 5 - Verifiera att sökningen fungerar {#step-5}

+++**Sökproblem?**

Symtomen kan vara att inga produkter, tomma kategorier eller att inga uppdateringar av produkter eller produktkategorier är korrekta.

a. JA - Kör det här kommandot för att kontrollera status för katalogsökning: `php bin/magento indexer:status`. Fortsätt till [Steg 8](#step-8).\
b. NO - Kör kommando: `php bin/magento config:show catalog/search/engine`. Fortsätt till [Steg 6](#step-6).

+++

## Steg 6 - Kontrollera ElasticSuite {#step-6}

+++**ElasticSuite används?**

a. JA - Kontrollera om ElasticSuite är i den aktuella versionen genom att köra det här kommandot: `cat composer.lock | grep -A 1 elasticsuite | grep '"version"'` Om du vill kontrollera om den här versionen är avskriven eller rekommenderad, se [Github: Le-SA/elaticsuite](https://github.com/Smile-SA/elasticsuite). Om ElasticSuite är uppdaterad fortsätter du till [Steg 10](#step-10).\
b. NEJ - fortsätt till [Steg 7](#step-7).

+++

## Steg 7 - Kontrollera att ECE-verktygen är aktuella {#step-7}

+++**Är ECE-verktygen den senaste versionen?**

Kör kommandot: `php ./vendor/bin/ece-tools -V` och kontrollera ECE-verktygens version. Är det [senaste versionen av ECE-verktygen](https://github.com/magento/ece-tools/releases)?

a. JA - Fortsätt till [Steg 5a](#step-5).\
b. NEJ - Uppgradera ECE-verktygen till den senaste versionen. Kör kommandot `php bin/magento config: show catalog/search/engine` för att kontrollera sökmotorn. Fortsätt till [Steg 6](#step-6).

+++

## Steg 8 - Sök efter omindexering {#step-8}

+++**Är katalogsökningsstatus i _Bearbetar_?**

a. JA - Du måste vänta tills bearbetningen är klar och sedan kontrollera om produktkategorierna har uppdaterats. Om de inte har det, [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NEJ - Om statusen för katalogsökningen är _Omindexering krävs_ kör i CLI/Terminal: `php bin/magento cron:run`. Om det inte fungerar kör du: `php bin/magento indexer:reindex`. Om detta inte löser problemet, [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Steg 9 - Kontrollera stavningskonfiguration {#step-9}

+++**`.yaml`uppdaterades filen nyligen?**

a. JA - Kontrollera `.yaml` Elasticsearch-konfiguration genom att referera till DevDocs [Konfigurera Elasticsearch: Aktivera Elasticsearch](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=elastic%20search%20yaml).\
b. NEJ - [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Steg 10 - Kontrollera om det finns spårningsindex {#step-10}

+++**Finns det spårningsindex listade?**

Kör `curl elasticsearch.internal:9200/_cat/indices` (om du arbetar i en integreringsmiljö som innehåller alla Starter-grenar). Om du använder testnings- eller produktionsmiljön i Pro kör du `curl localhost:9200/_cat/indices`. Finns det spårningsindex listade? Kontrollera utdata för`_tracking_log_`.

a. JA - Om du har en version av ElasticSuite som är tidigare än version 2.8.0 rekommenderar vi att du [uppgradera till ElasticSuite 2.8.0 för att justera kvarhållande av spårningsindex eller inaktivera spårning](https://support.magento.com/hc/en-us/articles/360035266131?). Om du inte kan uppgradera direkt kan du [skapa en kron för att ta bort spårningsindex](/help/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.md). Detta kan dock orsaka prestandaproblem. När du har uppgraderat till ElasticSuite 2.8.0 eller tagit bort spårningsindex kör du kommandot (om du använder testnings- eller produktionsmiljöer i Pro):`localhost:9200/_cat/allocation?v` för att kontrollera tillgängligt utrymme. Om du är i någon av integreringsmiljöerna (det vill säga alla startgrenar) kör du `elasticsearch.internal:9200/_cat/allocation?v`. Fortsätt till [Steg 11](#step-11).\
b. NO - Om du använder testmiljöer eller produktionsmiljöer i Pro kan du köra `localhost:9200/_cat/allocation?v` och kontrollera tillgängligt utrymme. Om du är i någon av integreringsmiljöerna (det vill säga alla startgrenar) kör du `elasticsearch.internal:9200/_cat/allocation?v`. Fortsätt till [Steg 11](#step-11).

+++

## Steg 11 - Sök efter specifikt fel {#step-11}

+++**Specifikt fel?**

Adobe Commerce och ES loggar, tillägg och anpassad kod.

a. JA - Läs Adobe Commerce Help Center Troubleshooting article [Kontrollera att Elasticsearch är korrekt installerat](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) eller [Elasticsearch kraschar eller har slut på minne när ElasticSuite-plugin används](https://support.magento.com/hc/en-us/articles/360035266131).\
b. NEJ - Fortsätt till [Steg 12](#step-12).

+++

## Steg 12 - Kontrollera tillgängligt lagringsutrymme {#step-12}

+++**Lagringsanvändning > 85 %?**

a. JA - Du måste öka det tillgängliga lagringsutrymmet. Se DevDocs[Konfigurera Elasticsearch: Aktivera Elasticsearch](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=elastic%20search%20yaml). Kör sedan: `localhost:9200/_cat/allocation?v` (om du använder testmiljöer eller produktionsmiljöer i Pro). Om du är i någon av integreringsmiljöerna (det vill säga alla Starter-grenar) kör du: `elasticsearch.internal:9200/_cat/allocation?v`. Fortsätt till [Steg 11](#step-11).\
b. NEJ - [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Tillbaka till steg 1](#step-1)
