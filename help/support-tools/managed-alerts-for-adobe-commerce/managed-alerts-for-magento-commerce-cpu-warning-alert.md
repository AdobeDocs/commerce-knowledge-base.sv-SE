---
title: "Hanterade varningar för Adobe Commerce: CPU-varning"
description: Den här artikeln innehåller felsökningssteg när du får en CPU-varning för Adobe Commerce i New Relic. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.
exl-id: 03686684-3b7e-430a-a05a-a96f38345322
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# Hanterade varningar för Adobe Commerce: CPU-varning

Den här artikeln innehåller felsökningssteg när du får en CPU-varning för Adobe Commerce i New Relic. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.

![CPU-varning](assets/cpu-warning-magento-managed.png){width="500"}

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur Pro planarkitektur

## Problem

Du får ett varningsmeddelande i New Relic om du har registrerat dig för [Hanterade aviseringar för Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) och ett eller flera av tröskelvärdena för larm har överskridits. Dessa varningar utvecklades av Adobe för att ge kunderna en standarduppsättning med hjälp av insikter från support och konstruktion.

<u> **Gör!** </u>

* Avbryt all schemalagd distribution tills den här aviseringen har rensats.
* Placera sajten i underhållsläge omedelbart om sajten inte svarar helt. Om du vill se steg går du till [Installationsguide > Aktivera eller inaktivera underhållsläge](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) i vår dokumentation för utvecklare. Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Om du vill se steg går du till [Underhåll listan över undantagna IP-adresser](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) i vår dokumentation för utvecklare.

<u>**Gör det inte!**</u>

* lansera fler marknadsföringskampanjer som kan ge er webbplats fler sidvisningar.
* Kör indexerare eller ytterligare kroner som kan orsaka ytterligare belastning på processorn eller disken.
* Utför några större administrativa uppgifter (t.ex. Commerce Admin, import/export av data).
* Rensa cachen.

## Lösning

Följ de här stegen för att identifiera och felsöka orsaken.

1. Använd [New Relic APM&#39;s Transaction page](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) för att identifiera transaktioner med prestandaproblem:
   * Sortera transaktioner efter stigande Apdex-poäng. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) avser hur nöjda användarna är med svarstiden för dina webbprogram och -tjänster. [Låga Apdex-poäng](/help/troubleshooting/miscellaneous/troubleshoot-performance-using-new-relic-on-magento-commerce.md#low_user_satisfaction) kan tyda på en flaskhals (en transaktion med en högre svarstid). Vanligtvis är det databasen, Redis eller PHP. Anvisningar finns i New Relic [Visa transaktioner med största missnöjd med Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Sortera transaktioner efter högsta genomströmning, långsammast genomsnittlig svarstid, mest tidskrävande och andra tröskelvärden. Anvisningar finns i New Relic [Hitta specifika prestandaproblem](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Om du fortfarande har svårt att identifiera källan ska du använda [Infrastruktursida för New Relic APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) för att identifiera resurskrävande tjänster. Anvisningar finns i New Relic [Värdsida för infrastrukturövervakning > fliken Processer](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Om du identifierar källan kommer SSH in i miljön för att undersöka ytterligare. Om du vill se steg går du till [Cloud for Adobe Commerce > SSH into your environment](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) i vår dokumentation för utvecklare.
1. Om du fortfarande har svårt att identifiera källan:
   * Granska de senaste trenderna för att identifiera problem med de senaste koddistributionerna eller konfigurationsändringarna (t.ex. nya kundgrupper och stora förändringar i katalogen). Vi rekommenderar att du granskar de senaste sju dagarnas aktivitet för att se eventuella samband i koddistributioner eller ändringar.
   * Du bör kontrollera och inaktivera platta kataloger. Om du vill se steg går du till [Långsamma prestanda, långsamma och långvariga kroner](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) i vår kunskapsbas för support.
   * Om du misstänker att du har en DDoS-attack kan du försöka blockera robottrafiken. Om du vill se steg går du till [Så här blockerar du skadlig trafik för Adobe Commerce på snabbnivå](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) i vår kunskapsbas för support.
1. Om problemet verkar vara tillfälligt utför du åtgärder som att uppgradera eller försätter platsen i underhållsläge. Om du vill se steg går du till [Så här begär du tillfällig storlek](/help/how-to/general/how-to-request-temporary-magento-upsize.md) i vår kunskapsbas och [Installationsguide > Aktivera eller inaktivera underhållsläge](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) i vår dokumentation för utvecklare. Om storleken på upp-sidan återställer webbplatsen till normal drift kan du begära en permanent uppstorlek (kontakta ditt Adobe-kontoteam) eller försöka återskapa problemet i din dedikerade mellanlagring genom att köra ett inläsningstest och optimera frågor, eller kod som minskar trycket på tjänsterna. Om du vill se steg går du till [Cloud for Adobe Commerce > Testa driftsättning > Läs in- och stresstestning](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) i vår dokumentation för utvecklare.
