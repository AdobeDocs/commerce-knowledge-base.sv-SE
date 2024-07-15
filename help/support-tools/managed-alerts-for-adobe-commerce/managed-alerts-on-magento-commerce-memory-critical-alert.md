---
title: 'Hanterade varningar på Adobe Commerce: minneskritisk varning'
description: Den här artikeln innehåller felsökningssteg när du får en minneskritisk varning för Adobe Commerce i New Relic. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.
exl-id: feed7998-c50b-4cbf-a92d-cbfc65745a1c
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 468ad1c47da3c299b8028726e79e25a4aa9489ea
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 0%

---

# Hanterade varningar på Adobe Commerce: minneskritisk varning

Den här artikeln innehåller felsökningssteg när du får en minneskritisk varning för Adobe Commerce i New Relic. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.

![Diskkritisk varning](assets/memory-critical-magento-managed.png){width="500"}

## Berörda produkter och versioner

Alla versioner av Adobe Commerce på Cloud Infrastructure Pro-planarkitekturen.

## Problem

Du får en hanterad avisering i New Relic om du har registrerat upp till [Hanterade aviseringar för Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) och ett eller flera av aviseringströskelvärdena har överskridits. Dessa varningar utvecklades av Adobe för att ge kunderna en standarduppsättning med hjälp av insikter från support och konstruktion.

<u> **Gör!** </u>

* Avbryt all schemalagd distribution tills den här aviseringen har rensats
* Placera platsen i underhållsläge omedelbart om platsen inte svarar eller inte svarar alls. Anvisningar finns i [Installationshandbok > Aktivera eller inaktivera underhållsläge](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) i utvecklardokumentationen. Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Anvisningar finns i [Underhåll listan över undantagna IP-adresser](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) i utvecklardokumentationen.

<u>**Gör inte!**</u>

* lansera fler marknadsföringskampanjer som kan ge er webbplats fler sidvisningar.
* Kör indexerare eller ytterligare kroner som kan orsaka ytterligare belastning på processorn eller disken.
* Utför några större administrativa uppgifter (t.ex. Commerce Admin, import/export av data).
* Rensa cachen.

Din webbplats kanske inte svarar (om du inte redan drabbas av ett avbrott i din webbplats) om du utför någon av åtgärderna&quot;Gör inte&quot; innan du har undersökt och löst orsaken till varningen.

## Lösning

Följ de här stegen för att identifiera och felsöka orsaken.

>[!WARNING]
>
>Eftersom det här är en viktig varning rekommenderar vi att du slutför **steg 1** innan du försöker felsöka problemet (steg 2 och framåt).

1. Kontrollera om Adobe Commerce supportanmälan finns. Anvisningar finns i [Spåra dina supportärenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) i vår kunskapsbas för support. Supporten kan redan ha fått en New Relic-tröskelvarning, skapat en biljett och börjat arbeta med problemet. Om det inte finns någon biljett skapar du en. Biljetten ska ha följande information:
   * Kontaktorsak: välj&quot;New Relic CRITICAL-varning mottagen&quot;
   * Beskrivning av aviseringen
   * [Länk till New Relic Incident](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Detta ingår i dina [hanterade aviseringar för Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).

1. Använd infrastruktursidan ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) för [New Relic APM för att identifiera de mest minnesintensiva processerna. Anvisningar om hur du gör detta finns på New Relic [värdsida för infrastrukturövervakning > fliken Processer](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes):
   * Om tjänster som Redis, MySQL eller PHP är de viktigaste källorna för minnesförbrukning kan du försöka med följande:
1. Kontrollera att du har de senaste versionerna. Nyare versioner kan ibland åtgärda minnesläckor. Om du inte har den senaste versionen bör du uppgradera. Anvisningar finns i [Adobe Commerce om molninfrastruktur > Tjänster > Ändra tjänster](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) i utvecklardokumentationen.
1. Om problemet med tjänsten inte är versionsrelaterat kan du försöka med följande:
1. **MySQL**: Sök efter problem som långvariga frågor, odefinierade primärnycklar och dubblettindex. Anvisningar finns i [De vanligaste databasproblemen i Adobe Commerce om molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) i vår kunskapsbas för support.
1. **Redis**: Om Redis är den främsta källan till minnesförbrukning [skickar du en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
1. **PHP**: Om PHP är den främsta källan till minnesförbrukning kan du granska processer som körs genom att köra `ps aufx` i CLI/Terminal. I slutversionen ser du de kroniska jobb och processer som körs. Kontrollera utdata för processernas körningstid. Om det finns en kron med lång exekveringstid kan kronen hänga. Felsökningssteg finns i [Långsamma prestanda, kron som körs långsamt och långt ](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) och [Kron-jobb som fastnat i körningsstatus](https://support.magento.com/hc/en-us/articles/360033099451) i vår kunskapsbas för support.
1. Om du fortfarande har problem med att identifiera orsaken till problemet kan du använda [New Relic APM:s transaktionssida](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) för att identifiera transaktioner med prestandaproblem:
   * Sortera transaktioner efter stigande Apdex-poäng. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) hänvisar till hur nöjda användarna är med svarstiden för dina webbprogram och tjänster. En [låg Apdex-poäng](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) kan indikera en flaskhals (en transaktion med en högre svarstid). Vanligtvis är det databasen, Redis eller PHP. Anvisningar om hur du gör detta finns i New Relic [Visa transaktioner med högst missnöjd med apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Sortera transaktioner efter högsta genomströmning, den långsammaste genomsnittliga svarstiden, den mest tidskrävande och andra tröskelvärden. Anvisningar finns i New Relic [Hitta specifika prestandaproblem](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Om du fortfarande har svårt att identifiera problemet kan du använda infrastruktursidan för New Relic APM.
1. Om du inte kan identifiera orsaken till den ökade minnesanvändningen kan du granska aktuella trender för att identifiera problem med nyligen använda koddistributioner eller konfigurationsändringar (till exempel nya kundgrupper och stora ändringar i katalogen). Vi rekommenderar att du granskar de senaste 7 dagarnas aktivitet för att se om det finns några korrelationer i koddistributioner eller ändringar.
1. Om ovanstående metoder inte hjälper dig att hitta orsaken och/eller lösningen inom rimlig tid, begär du en uppgradering eller placerar platsen i underhållsläge om du inte redan har gjort det. Anvisningar om hur du gör finns i [Begär tillfällig storleksändring](/help/how-to/general/how-to-request-temporary-magento-upsize.md) i vår supportkunskapsbas och [Installationshandbok > Aktivera eller inaktivera underhållsläge](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) i utvecklardokumentationen.
1. Om storleken på upp-sidan återställer webbplatsen till normal drift kan du begära en permanent storlek (kontakta ditt Adobe-kontoteam) eller försöka återskapa problemet i din dedikerade mellanlagring genom att köra ett inläsningstest och optimera frågor, eller kod som minskar trycket på tjänsterna. Se [Adobe Commerce om molninfrastruktur > Testa distribution > Läs in och stresstestning](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) i vår utvecklardokumentation.
