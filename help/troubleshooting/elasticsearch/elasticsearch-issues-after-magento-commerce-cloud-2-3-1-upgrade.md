---
title: Problem med Elasticsearch efter uppgraderingen av Adobe Commerce molninfrastruktur 2.3.1+
description: I den här artikeln beskrivs en lösning på problem under distributionen efter uppgradering till Adobe Commerce i molninfrastrukturversionerna 2.3.1+, om du använder Elasticsearch version 2.x och 5.x.
exl-id: 6ceeb2ea-528d-4c03-ab2b-c5aed46fd0a2
feature: Cloud
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Problem med Elasticsearch efter uppgraderingen av Adobe Commerce molninfrastruktur 2.3.1+

>[!WARNING]
>
>[MySQL-katalogsökmotorn tas bort i Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Du måste ha konfigurerat värddatorn Elasticsearch innan du kan installera version 2.4.0. Se [Installera och konfigurera Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html).

>[!WARNING]
>
>Observera att serviceuppgraderingar inte kan föras över till produktionsmiljön utan att vårt infrastrukturteam underrättas inom 48 timmar. Detta är nödvändigt eftersom vi måste se till att det finns en infrastruktursupporttekniker tillgänglig som kan uppdatera din konfiguration inom en önskad tidsram med minimala driftavbrott i din produktionsmiljö. Så 48 timmar före när dina ändringar behöver vara i produktion [skickar du en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) med information om den nödvändiga uppgraderingen och den tidpunkt då du vill att uppgraderingen ska starta.

I den här artikeln beskrivs en lösning på problem under distributionen efter uppgradering till Adobe Commerce i molninfrastrukturversionerna 2.3.1+, om du använder Elasticsearch version 2.x och 5.x.

## Berörda produkter och versioner:

* Adobe Commerce om molninfrastruktur 2.3.1+
* Elasticsearch 2.x och 5.x

## Orsak

Handlare som har uppgraderat till Adobe Commerce i molninfrastruktur (version 2.3.1 och senare) och som använder en tidigare version av Elasticsearch än version 6.x kan råka ut för fel vid distributionen. Detta beror på att Elasticsearch version 2.x och 5.x är [End of Life](https://www.elastic.co/support/eol) och inte längre stöds i Adobe Commerce. Elasticsearch-klienten måste vara uppdaterad eller köra en distributionsrisk som utlöser ett fel. Mer information finns i [Ändra Elasticsearch-klienten](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html) i utvecklardokumentationen.

## Problem

När du distribuerar ser du ett felmeddelande som liknar följande, som anger att din Elasticsearch-version inte är kompatibel: *Elasticsearch-tjänstversion 5.2.2 på infrastrukturskiktet är inte kompatibel med den aktuella versionen av modulen elasticsearch/elasticsearch (6.7.0.0), som används av ditt Magento-program.* *Du kan åtgärda det här problemet genom att uppgradera Elasticsearch-tjänsten på din Magento Cloud-infrastruktur till version 6.x*. Andra symtom på det här problemet kan vara saknade bilder och problem med filter i din miljö.

## Lösning

>[!WARNING]
>
>Om du har en delad miljö måste du se till att mellanlagring och produktion är klara att uppgraderas.

För att lösa detta problem måste klientmodulen och tjänsten Elasticsearch finnas på de senaste rekommenderade versionerna av Elasticsearch:

1. Följ instruktionerna för att [ändra modulen Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html) i utvecklardokumentationen så att du har den senaste rekommenderade versionen av klientmodulen Elasticsearch.
1. [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) och begär en Elasticsearch-tjänstuppdatering till 6.x för testning och produktion. Observera att det kan ta lite tid att uppgradera till Elasticsearch.

## Relaterad läsning

* [Krav för teknikhög i Adobe Commerce 2.3](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements-tech.html) i utvecklardokumentationen.
* [Konfigurera tjänsten Elasticsearch](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html) i utvecklardokumentationen.
* [Installera och konfigurera Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html) i utvecklardokumentationen.
* [Kontrollera att Elasticsearch är korrekt installerat](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) i vår kunskapsbas för support.
