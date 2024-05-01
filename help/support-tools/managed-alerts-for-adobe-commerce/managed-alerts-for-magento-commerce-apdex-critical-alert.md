---
title: 'Hanterade aviseringar för Adobe Commerce: ADOBE-kritisk avisering'
description: I den här artikeln beskrivs felsökningssteg när du får en varning om att Adobe Commerce i New Relic är mycket viktig för Apdex. Poängen i Apdex mäter hur nöjda användarna är med svarstiden för webbprogram och tjänster. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.
exl-id: b6d3d4f3-4abb-4285-8071-2b9fb06bfa3c
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: fbb24fb3c8b399f3b7e19c663eb4b168657498e6
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 0%

---

# Hanterade aviseringar för Adobe Commerce: ADOBE-varning

I den här artikeln beskrivs felsökningssteg när du får en varning om att Adobe Commerce i New Relic är mycket viktig för Apdex. Poängen i Apdex mäter hur nöjda användarna är med svarstiden för webbprogram och tjänster. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.

![praktisk kritisk varning](assets/apdex-critical-magento-managed.png){width="500"}

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur Pro planarkitektur
* Adobe Commerce om molninfrastruktur - arkitektur för Starter-plan

## Problem

Du får en hanterad avisering i New Relic om du har registrerat dig för [Hanterade aviseringar för Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) och ett eller flera av tröskelvärdena för larm har överskridits. Dessa varningar utvecklades av Adobe för att ge säljarna en standarduppsättning med hjälp av insikter från support och konstruktion.

<u> **Gör!** </u>

* Avbryt all schemalagd distribution tills den här aviseringen har rensats.
* Placera platsen i underhållsläge omedelbart om platsen inte svarar eller inte svarar alls. Om du vill se steg går du till [Installationsguide > Aktivera eller inaktivera underhållsläge](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) i vår dokumentation för utvecklare. Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Om du vill se steg går du till [Underhåll listan över undantagna IP-adresser](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) i vår dokumentation för utvecklare.

<u>**Gör det inte!**</u>

* lansera fler marknadsföringskampanjer som kan ge er webbplats fler sidvisningar.
* Kör indexerare eller ytterligare kroner som kan orsaka ytterligare belastning på processorn eller disken.
* Utför några större administrativa uppgifter (t.ex. Commerce Admin, import/export av data).
* Rensa cachen.

Om du gör det ovan när du har fått en viktig varning, innan du har felsökt orsaken till aviseringen, kan det leda till att din webbplats inte svarar om du inte redan har ett avbrott i din webbplats.

## Lösning

Följ de här stegen för att identifiera och felsöka orsaken.

>[!WARNING]
>
>Eftersom detta är en viktig varning rekommenderar vi att du slutför **Steg 1** innan du försöker felsöka problemet (steg 2 och framåt).

1. Kontrollera om Adobe Commerce supportanmälan finns. Om du vill se steg går du till [Spåra era supportärenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) i vår kunskapsbas för support. Supporten kan ha tagit emot en New Relic-tröskelvarning, skapat en biljett och börjat arbeta med problemet. Om det inte finns någon biljett skapar du en. Biljetten ska ha följande information:
   * Kontaktorsak: välj&quot;New Relic CRITICAL-varning mottagen&quot;.
   * Beskrivning av aviseringen.
   * [Länk till New Relic Incident](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Detta ingår i [Hanterade aviseringar för Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Identifiera källan till problemet med hjälp av [New Relic APM&#39;s Transaction page](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) för att identifiera transaktioner med prestandaproblem:
   * Sortera transaktioner efter stigande Apdex-poäng. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) avser hur nöjda användarna är med svarstiden för dina webbprogram och -tjänster. En låg Apdex-poäng kan tyda på en flaskhals (en transaktion med en högre svarstid). Vanligtvis är det databasen, Redis eller PHP. Anvisningar finns i New Relic [Visa transaktioner med största missnöjd med Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction/#dissatisfaction).
   * Sortera transaktioner efter högsta genomströmning, den långsammaste genomsnittliga svarstiden, den mest tidskrävande och andra tröskelvärden. Anvisningar finns i New Relic [Hitta specifika prestandaproblem](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Om du fortfarande har svårt att identifiera problemet kan du använda infrastruktursidan för New Relic APM.
1. Använd [Infrastruktursida för New Relic APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) för att identifiera resursintensiva processer. Anvisningar finns i New Relic [Värdsida för infrastrukturövervakning > fliken Processer](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Om tjänster som Redis eller MySQL är den främsta källan för minnesförbrukning kan du försöka med följande:
   * Kontrollera att du har den senaste versionen. Nyare versioner kan ibland åtgärda minnesläckor. Om du inte har den senaste versionen bör du uppgradera. Om du vill se steg går du till [Cloud för Adobe Commerce > Tjänster > Ändra tjänster](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) i vår dokumentation för utvecklare.
   * Kontrollera om det finns MySQL-problem som långvariga frågor, odefinierade primärnycklar och dubblerade index. Om du vill se steg går du till [De vanligaste databasproblemen i Adobe Commerce om molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) i vår dokumentation för utvecklare.
   * Sök efter PHP-problem. Granska pågående processer genom att köra `ps aufx` i CLI/Terminal. I slutversionen ser du de kroniska jobb och processer som körs. Kontrollera utdata för processernas körningstid. Om det finns en kron med lång exekveringstid kan kronen hänga. Felsökningssteg finns i [Långsamma prestanda, långsamma och långvariga kroner](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) och [Kronjobbet fastnade i körningsstatus](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md) i vår kunskapsbas för support.

1. När källan har identifierats kan SSH ta sig in i miljön för att undersöka ytterligare. Om du vill se steg går du till [Cloud for Adobe Commerce > Teknik och krav > SSH i din miljö](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) i vår dokumentation för utvecklare.
1. Om du fortfarande har svårt att identifiera källan bör du granska de senaste trenderna för att identifiera problem med nyligen använda koddistributioner eller konfigurationsändringar (till exempel nya kundgrupper och stora ändringar i katalogen). Vi rekommenderar att du granskar de senaste sju dagarnas aktivitet för att se eventuella samband i koddistributioner eller ändringar.
1. Om du inte kan hitta en lösning inom rimlig tid kan du begära en uppgradering eller placera platsen i underhållsläge om du inte redan har gjort det. Om du vill se steg går du till [Så här begär du tillfällig storlek](/help/how-to/general/how-to-request-temporary-magento-upsize.md) i vår kunskapsbas och [Installationsguide > Aktivera eller inaktivera underhållsläge](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) i vår dokumentation för utvecklare.
1. Om storleken på upp-sidan återställer webbplatsen till normal drift kan du begära en permanent storlek (kontakta ditt Adobe-kontoteam) eller försöka återskapa problemet i din dedikerade mellanlagring genom att köra ett inläsningstest och optimera frågor, eller kod som minskar trycket på tjänsterna. Se [Cloud for Adobe Commerce > Testa driftsättning > Läs in- och stresstestning](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) i vår dokumentation för utvecklare.
