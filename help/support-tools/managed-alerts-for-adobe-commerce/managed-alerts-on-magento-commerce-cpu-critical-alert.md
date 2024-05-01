---
title: 'Hanterade varningar på Adobe Commerce: CPU-kritisk varning'
description: I den här artikeln beskrivs felsökningssteg när du får en viktig processorvarning för Adobe Commerce i New Relic. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.
exl-id: 45b8ced0-b12f-428b-9838-2a9c26b9874b
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 5be8f2969426078bfcc0e4ffb4895dcf0327165f
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 0%

---

# Hanterade varningar på Adobe Commerce: CPU-kritisk varning

I den här artikeln beskrivs felsökningssteg när du får en viktig processorvarning för Adobe Commerce i New Relic. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.

![diskkritisk varning](assets/cpu-critical-magento-managed.png){width="500"}

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur Pro planarkitektur

## Problem

Du får en hanterad avisering i New Relic om du har registrerat dig för [Hanterade aviseringar för Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) och ett eller flera av tröskelvärdena för larm har överskridits. Dessa varningar har utvecklats av Adobe Commerce för att ge kunderna en standarduppsättning med hjälp av insikter från support och konstruktion.

<u>**Gör!**</u>:

* Avbryt all schemalagd distribution tills den här aviseringen har rensats.
* Placera platsen i underhållsläge omedelbart om platsen inte svarar eller inte svarar alls. Om du vill se steg går du till [Installationsguide > Aktivera eller inaktivera underhållsläge](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) i vår dokumentation för utvecklare. Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Om du vill se steg går du till [Underhåll listan över undantagna IP-adresser](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) i vår dokumentation för utvecklare.

<u>**Gör det inte!**</u>:

* lansera fler marknadsföringskampanjer som kan ge er webbplats fler sidvisningar.
* Kör indexerare eller ytterligare kroner, vilket kan orsaka extra belastning på processorn eller disken.
* Utför några större administrativa uppgifter (t.ex. Commerce Admin, import/export av data).
* Rensa cachen.

Din webbplats kanske inte svarar (om du inte redan har ett avbrott i din webbplats) om du utför någon av åtgärderna&quot;Gör inte&quot; innan du har undersökt och löst orsaken till varningen.

## Lösning

Följ de här stegen för att identifiera och felsöka orsaken.

>[!WARNING]
>
>Eftersom detta är en viktig varning rekommenderar vi att du slutför **Steg 1** innan du försöker felsöka problemet (steg 2 och framåt).

Kontrollera om Adobe Commerce supportanmälan finns. Om du vill se steg går du till [Spåra era supportärenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) i vår kunskapsbas för support. Supporten kan ha tagit emot en New Relic-tröskelvarning, skapat en biljett och börjat arbeta med problemet. Om det inte finns någon biljett skapar du en. Biljetten ska ha följande information:

1. Kontaktorsak: välj&quot;New Relic CRITICAL-varning mottagen&quot;.
1. Beskrivning av aviseringen.
1. [Länk till New Relic Incident](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Detta ingår i [Hanterade aviseringar för Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Använd [New Relic APM&#39;s Transaction page](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) för att identifiera transaktioner med prestandaproblem:
   * Sortera transaktioner efter stigande Apdex-poäng. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) avser hur nöjda användarna är med svarstiden för dina webbprogram och -tjänster. A [low Apdex score](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) kan tyda på en flaskhals (en transaktion med en högre svarstid). Vanligtvis är den relaterad till databasen, Redis eller PHP. Anvisningar finns i New Relic [Visa transaktioner med största missnöjd med Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Sortera transaktioner efter högsta genomströmning, långsammast genomsnittlig svarstid, mest tidskrävande och andra tröskelvärden. Anvisningar finns i New Relic [Hitta specifika prestandaproblem](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Om du fortfarande har svårt att identifiera källan ska du använda [Infrastruktursida för New Relic APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page) för att identifiera resurskrävande tjänster. Anvisningar finns i New Relic [Värdsida för infrastrukturövervakning > fliken Processer](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Om du identifierar källan kommer SSH in i miljön för att undersöka ytterligare. Om du vill se steg går du till [SSH i din miljö för Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) i vår dokumentation för utvecklare.
1. Om du fortfarande har svårt att identifiera källan:
   * Granska de senaste trenderna för att identifiera problem med de senaste koddistributionerna eller konfigurationsändringarna (t.ex. nya kundgrupper och stora förändringar i katalogen). Vi rekommenderar att du granskar de senaste sju dagarnas aktivitet för att se eventuella samband i koddistributioner eller ändringar.
   * Du bör kontrollera och inaktivera platta kataloger. Om du vill se steg går du till [Långsamma prestanda, långsamma och långvariga kroner](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) i vår kunskapsbas för support.
   * Om du misstänker att du har en DDoS-attack kan du försöka blockera robottrafiken. Om du vill se steg går du till [Så här blockerar du skadlig trafik för Adobe Commerce i molninfrastrukturen på snabbnivå](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) i vår kunskapsbas för support.
1. Om problemet verkar vara tillfälligt utför du åtgärder som att uppgradera eller försätter platsen i underhållsläge. Om du vill se steg går du till [Så här begär du tillfällig storlek](/help/how-to/general/how-to-request-temporary-magento-upsize.md) i vår kunskapsbas och [Installationsguide > Aktivera eller inaktivera underhållsläge](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) i vår dokumentation för utvecklare. Om storleken på upp-sidan återställer webbplatsen till normal drift kan du begära en permanent uppstorlek (kontakta ditt Adobe-kontoteam) eller försöka återskapa problemet i din dedikerade mellanlagring genom att köra ett inläsningstest och optimera frågor eller kod som minskar trycket på tjänsterna. Om du vill se steg går du till [Testa driftsättning > Belastnings- och stresstestning](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) i vår utvecklardokumentation för Adobe Commerce om molninfrastruktur.
