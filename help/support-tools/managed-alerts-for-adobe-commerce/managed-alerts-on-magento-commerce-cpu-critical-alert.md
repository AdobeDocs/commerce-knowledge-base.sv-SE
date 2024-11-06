---
title: 'Hanterade varningar på Adobe Commerce: CPU-kritisk varning'
description: I den här artikeln beskrivs felsökningssteg när du får en viktig processorvarning för Adobe Commerce i New Relic. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.
exl-id: 45b8ced0-b12f-428b-9838-2a9c26b9874b
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 0%

---

# Hanterade varningar på Adobe Commerce: CPU-kritisk varning

I den här artikeln beskrivs felsökningssteg när du får en viktig processorvarning för Adobe Commerce i New Relic. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.

![Diskkritisk varning](assets/cpu-critical-magento-managed.png){width="500"}

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur Pro planarkitektur

## Problem

Du får en hanterad avisering i New Relic om du har registrerat upp till [Hanterade aviseringar för Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) och ett eller flera av aviseringströskelvärdena har överskridits. Dessa varningar har utvecklats av Adobe Commerce för att ge kunderna en standarduppsättning med hjälp av insikter från support och konstruktion.

<u>**Gör!**</u>:

* Avbryt all schemalagd distribution tills den här aviseringen har rensats.
* Placera platsen i underhållsläge omedelbart om platsen inte svarar eller inte svarar alls. Anvisningar finns i [Installationshandboken > Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i utvecklardokumentationen. Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Anvisningar finns i [Underhåll listan över undantagna IP-adresser](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt) i utvecklardokumentationen.

<u>**Gör inte!**</u>:

* lansera fler marknadsföringskampanjer som kan ge er webbplats fler sidvisningar.
* Kör indexerare eller ytterligare kroner, vilket kan orsaka extra belastning på processorn eller disken.
* Utför några större administrativa uppgifter (t.ex. Commerce Admin, import/export av data).
* Rensa cachen.

Din webbplats kanske inte svarar (om du inte redan har ett avbrott i din webbplats) om du utför någon av åtgärderna&quot;Gör inte&quot; innan du har undersökt och löst orsaken till varningen.

## Lösning

Följ de här stegen för att identifiera och felsöka orsaken.

>[!WARNING]
>
>Eftersom det här är en viktig varning rekommenderar vi att du slutför **steg 1** innan du försöker felsöka problemet (steg 2 och framåt).

Kontrollera om Adobe Commerce supportanmälan finns. Anvisningar finns i [Spåra dina supportärenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) i vår kunskapsbas för support. Supporten kan ha tagit emot en New Relic-tröskelvarning, skapat en biljett och börjat arbeta med problemet. Om det inte finns någon biljett skapar du en. Biljetten ska ha följande information:

1. Kontaktorsak: välj&quot;New Relic CRITICAL-varning mottagen&quot;.
1. Beskrivning av aviseringen.
1. [Länk till New Relic Incident](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Detta ingår i dina [hanterade aviseringar för Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Använd [New Relic APM:s transaktionssida](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) för att identifiera transaktioner med prestandaproblem:
   * Sortera transaktioner efter stigande Apdex-poäng. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) hänvisar till hur nöjda användarna är med svarstiden för dina webbprogram och tjänster. En [låg Apdex-poäng](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) kan indikera en flaskhals (en transaktion med en högre svarstid). Vanligtvis är den relaterad till databasen, Redis eller PHP. Anvisningar om hur du gör detta finns i New Relic [Visa transaktioner med högst missnöjd med apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Sortera transaktioner efter högsta genomströmning, långsammast genomsnittlig svarstid, mest tidskrävande och andra tröskelvärden. Anvisningar finns i New Relic [Hitta specifika prestandaproblem](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Om du fortfarande har problem med att identifiera källan använder du [New Relic APM:s infrastruktursida](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page) för att identifiera resurskrävande tjänster. Anvisningar om hur du gör detta finns på sidan New Relic [Värdar för infrastrukturövervakning > fliken Processer](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Om du identifierar källan kommer SSH in i miljön för att undersöka ytterligare. Anvisningar om hur du gör detta finns i [SSH i din miljö för Adobe Commerce om molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) i utvecklardokumentationen.
1. Om du fortfarande har svårt att identifiera källan:
   * Granska de senaste trenderna för att identifiera problem med de senaste koddistributionerna eller konfigurationsändringarna (t.ex. nya kundgrupper och stora förändringar i katalogen). Vi rekommenderar att du granskar de senaste sju dagarnas aktivitet för att se eventuella samband i koddistributioner eller ändringar.
   * Du bör kontrollera och inaktivera platta kataloger. Anvisningar om hur du gör detta finns i [Långsamma prestanda, långsamma och långvariga kroner](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) i vår kunskapsbas för support.
   * Om du misstänker att du har en DDoS-attack kan du försöka blockera robottrafiken. Anvisningar finns i [Så här blockerar du skadlig trafik för Adobe Commerce på molninfrastruktur på snabbnivå](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) i vår kunskapsbas för support.
1. Om problemet verkar vara tillfälligt utför du åtgärder som att uppgradera eller försätter platsen i underhållsläge. Anvisningar finns i [Så här begär du tillfällig storleksändring](/help/how-to/general/how-to-request-temporary-magento-upsize.md) i vår supportkunskapsbas och [Installationshandbok > Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i utvecklardokumentationen. Om storleken på upp-sidan återställer webbplatsen till normal drift kan du begära en permanent uppstorlek (kontakta ditt Adobe-kontoteam) eller försöka återskapa problemet i din dedikerade mellanlagring genom att köra ett inläsningstest och optimera frågor eller kod som minskar trycket på tjänsterna. Anvisningar finns i [Testa distribution > Läs in och stresstestning](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) i utvecklardokumentationen för Adobe Commerce om molninfrastruktur.
