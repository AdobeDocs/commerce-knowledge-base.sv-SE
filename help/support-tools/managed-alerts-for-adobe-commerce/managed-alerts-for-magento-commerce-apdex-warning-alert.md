---
title: 'Hanterade aviseringar för Adobe Commerce: Apdex-varning'
description: I den här artikeln beskrivs felsökningssteg för när du får en Apdex-varning för Adobe Commerce i New Relic. Poängen i Apdex mäter hur nöjda användarna är med svarstiden för webbprogram och tjänster. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.
exl-id: 6e3f28ae-734b-468f-b6a5-c4f2edb1cb4b
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 0%

---

# Hanterade aviseringar för Adobe Commerce: Adexvarning

I den här artikeln beskrivs felsökningssteg för när du får en Apdex-varning för Adobe Commerce i New Relic. Poängen i Apdex mäter hur nöjda användarna är med svarstiden för webbprogram och tjänster. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.

![apdex-varning](assets/apdex-warning-magento-managed.png){width="500"}

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur Pro planarkitektur
* Adobe Commerce om molninfrastruktur - arkitektur för Starter-plan

## Problem

Du får en hanterad avisering i New Relic om du har registrerat upp till [Hanterade aviseringar för Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) och ett eller flera av aviseringströskelvärdena har överskridits. Dessa varningar utvecklades av Adobe för att ge säljarna en standarduppsättning med hjälp av insikter från support och konstruktion.

<u> **Gör!** </u>

* Avbryt all schemalagd distribution tills den här aviseringen har rensats.
* Placera platsen i underhållsläge omedelbart om platsen inte svarar eller inte svarar alls. Anvisningar finns i [Installationshandboken > Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i utvecklardokumentationen. Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Anvisningar finns i [Underhåll listan över undantagna IP-adresser](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt) i utvecklardokumentationen.

<u>**Gör inte!**</u>

* lansera fler marknadsföringskampanjer som kan ge er webbplats fler sidvisningar.
* Kör indexerare eller ytterligare kroner som kan orsaka ytterligare belastning på processorn eller disken.
* Utför några större administrativa uppgifter (t.ex. Commerce Admin, import/export av data).
* Rensa cachen.

## Lösning

Följ de här stegen för att identifiera och felsöka orsaken.

1. Identifiera källan till problemet genom att använda [New Relic APM:s transaktionssida](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) för att identifiera transaktioner med prestandaproblem:
   * Sortera transaktioner efter stigande Apdex-poäng. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) hänvisar till hur nöjda användarna är med svarstiden för dina webbprogram och tjänster. En [låg Apdex-poäng](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) kan indikera en flaskhals (en transaktion med en högre svarstid). Vanligtvis är det databasen, Redis eller PHP. Anvisningar om hur du gör detta finns i New Relic [Visa transaktioner med högst missnöjd med apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Sortera transaktioner efter högsta genomströmning, den långsammaste genomsnittliga svarstiden, den mest tidskrävande och andra tröskelvärden. Anvisningar finns i New Relic [Hitta specifika prestandaproblem](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Använd infrastruktursidan ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) för [New Relic APM för att identifiera resurskrävande processer. Anvisningar om hur du gör detta finns på sidan New Relic [Värdar för infrastrukturövervakning > fliken Processer](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Om tjänster som Redis eller MySQL är den främsta källan för minnesförbrukning kan du försöka med följande:
   * Kontrollera att du har den senaste versionen. Nyare versioner kan ibland åtgärda minnesläckor. Om du inte har den senaste versionen bör du uppgradera. Anvisningar finns i [Cloud för Adobe Commerce > Tjänster > Ändra tjänster](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) i utvecklardokumentationen.
1. Om problemet inte orsakas av tjänstversioner:
   * Kontrollera om det finns andra MySQL-problem, som långvariga frågor, odefinierade primärnycklar och dubblerade index. Anvisningar finns i [De vanligaste databasproblemen i Adobe Commerce om molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) i vår kunskapsbas för support.
   * Sök efter andra PHP-problem. Granska pågående processer genom att köra `ps aufx` i CLI/Terminal. I slutversionen ser du de kroniska jobb och processer som körs. Kontrollera utdata för processernas körningstid. Om det finns en kron med lång exekveringstid kan kronen hänga. Felsökningssteg finns i [Långsamma prestanda, långsamma och långvariga kroner](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) och [Kronjobb som fastnat i körningsstatus](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md) i vår kunskapsbas för support.
1. När en potentiell källa till problemet har identifierats kan SSH ta sig in i miljön för att undersöka saken ytterligare. Anvisningar om hur du gör detta finns i [Cloud for Adobe Commerce > Technologies and requirements > SSH into your environment](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) i vår utvecklardokumentation.
1. Om du fortfarande har svårt att identifiera källan bör du granska de senaste trenderna för att identifiera problem med nyligen använda koddistributioner eller konfigurationsändringar (till exempel nya kundgrupper och stora ändringar i katalogen). Vi rekommenderar att du granskar de senaste sju dagarnas aktivitet för att se eventuella samband i koddistributioner eller ändringar.
1. Om du inte kan hitta en lösning inom rimlig tid kan du begära en uppgradering eller placera platsen i underhållsläge om du inte redan har gjort det. Anvisningar finns i [Så här begär du tillfällig storleksändring](/help/how-to/general/how-to-request-temporary-magento-upsize.md) i vår kunskapsbas för support och [Installationshandbok > Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i utvecklardokumentationen.
1. Om [upsize](/help/how-to/general/how-to-request-temporary-magento-upsize.md) återställer webbplatsen till normal drift kan du begära en permanent uppstorlek (kontakta ditt Adobe-kontoteam) eller försöka återskapa problemet i din dedikerade mellanlagring genom att köra ett inläsningstest och optimera frågor eller kod som minskar trycket på tjänsterna. Mer information finns i [Cloud for Adobe Commerce > Testa distribution > Läs in och stresstesta](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) i utvecklardokumentationen.
