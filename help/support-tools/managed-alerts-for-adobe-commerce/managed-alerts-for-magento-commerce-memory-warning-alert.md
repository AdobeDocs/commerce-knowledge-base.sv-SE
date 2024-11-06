---
title: 'Hanterade aviseringar för Adobe Commerce: minnesvarning'
description: I den här artikeln beskrivs felsökningssteg för när du får en minnesvarning för Adobe Commerce i New Relic. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.
exl-id: bb5eb3f4-b162-4737-93d5-4037f2844bb1
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 0%

---

# Hanterade varningar för Adobe Commerce: minnesvarning

I den här artikeln beskrivs felsökningssteg för när du får en minnesvarning för Adobe Commerce i New Relic. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.

![minnesvarning](assets/memory-warning-magento-managed.png){width="500"}

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur Pro planarkitektur

## Problem

Du får en avisering i New Relic om du har registrerat upp till [Hanterade aviseringar för Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) och ett eller flera av aviseringströskelvärdena har överskridits. Dessa varningar har utvecklats av Adobe Commerce för att ge kunderna en standarduppsättning med hjälp av insikter från support och konstruktion.

<u>**Gör!**</u>:

* Vi rekommenderar att du avbryter alla schemalagda distributioner tills den här aviseringen har rensats.
* Placera platsen i underhållsläge omedelbart om platsen inte svarar eller inte svarar alls. Anvisningar finns i [Installationshandboken > Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i utvecklardokumentationen. Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Anvisningar finns i [Underhåll listan över undantagna IP-adresser](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt) i utvecklardokumentationen.

<u>**Gör inte!**</u>:

* lansera fler marknadsföringskampanjer som kan ge er webbplats fler sidvisningar.
* Kör indexerare eller ytterligare kroner, vilket kan orsaka extra belastning på processorn eller disken.
* Utför några större administrativa uppgifter (dvs. administratören, import/export av data).
* Rensa cachen.

## Lösning

Följ de här stegen för att identifiera och felsöka orsaken.

1. Använd infrastruktursidan ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) för [New Relic APM för att identifiera de mest minnesintensiva processerna. Anvisningar om hur du gör detta finns på sidan New Relic [Värdar för infrastrukturövervakning > fliken Processer](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes). Om tjänster som Redis eller MySQL är den främsta källan för minnesförbrukning kan du försöka med följande:

   * Kontrollera att du har den senaste versionen. Nyare versioner kan ibland åtgärda minnesläckor. Om du inte har den senaste versionen bör du uppgradera. Anvisningar finns i [Adobe Commerce om molninfrastruktur > Tjänster > Ändra tjänster](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) i utvecklardokumentationen.
   * Om du fortfarande inte kan identifiera källan till ökad minnesförbrukning söker du efter MySQL-problem som långvariga frågor, odefinierade primärnycklar och dubblerade index. Anvisningar finns i [De vanligaste databasproblemen i Adobe Commerce om molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) i vår kunskapsbas för support.
   * Om det inte finns några MySQL-problem söker du efter PHP-problem. Granska pågående processer genom att köra `ps aufx` i CLI/Terminal. I slutversionen ser du vilka kroniska jobb och processer som körs. Kontrollera utdata för processernas körningstid. Om det finns en kron med lång exekveringstid kan kronen hänga. Se [Låga prestanda, långsamma och långvariga kroner](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) och [Cron-jobb som fastnat i körningsstatus](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md) i vår supportkunskapsbas för felsökningssteg.

1. Om du fortfarande har problem med att identifiera orsaken till problemet kan du använda [New Relic APM:s transaktionssida](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) för att identifiera transaktioner med prestandaproblem:

   * Sortera transaktioner efter stigande Apdex-poäng. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) hänvisar till hur nöjda användarna är med svarstiden för dina webbprogram och tjänster. En [låg Apdex-poäng](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) kan indikera en flaskhals (en transaktion med en högre svarstid). Vanligtvis är det databasen, Redis eller PHP. Anvisningar om hur du gör detta finns i New Relic [Visa transaktioner med högst missnöjd med apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Sortera transaktioner efter högsta genomströmning, den långsammaste genomsnittliga svarstiden, den mest tidskrävande och andra tröskelvärden. Anvisningar finns i New Relic [Hitta specifika prestandaproblem](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Om du fortfarande har svårt att identifiera problemet kan du använda infrastruktursidan för New Relic APM.

1. Om du inte kan identifiera orsaken till den ökade minnesanvändningen kan du granska aktuella trender för att identifiera problem med nyligen använda koddistributioner eller konfigurationsändringar (till exempel nya kundgrupper och stora ändringar i katalogen). Vi rekommenderar att du granskar de senaste sju dagarnas aktivitet för att se eventuella samband i koddistributioner eller ändringar.

1. Om ovanstående metoder inte hjälper dig att hitta orsaken och/eller lösningen inom rimlig tid, begär du en uppgradering eller placerar platsen i underhållsläge om du inte redan har gjort det. Anvisningar finns i [Så här begär du tillfällig storleksändring](/help/how-to/general/how-to-request-temporary-magento-upsize.md) i vår supportkunskapsbas och [Installationshandbok > Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i utvecklardokumentationen.

1. Om storleken på upp-sidan återställer webbplatsen till normal drift kan du begära en permanent storlek (kontakta ditt Adobe-kontoteam) eller försöka återskapa problemet i din dedikerade mellanlagring genom att köra ett inläsningstest och optimera frågor, eller kod som minskar trycket på tjänsterna. Mer information finns i [Adobe Commerce om molninfrastruktur > Testa distribution > Läs in och stresstestning](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) i utvecklardokumentationen.
