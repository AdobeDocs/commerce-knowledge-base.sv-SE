---
title: 'Hanterade aviseringar om Adobe Commerce: MariaDB-aviseringar'
description: '"I den här artikeln beskrivs felsökningssteg när du får MariaDB-aviseringar för Adobe Commerce i New Relic. MariaDB-varningarna övervakar hög frågebelastning och överdrivna DML-frågor (Data Manipulation Language). Båda kan leda till en försämrad användarupplevelse eller till och med till driftstopp. Du kan få fyra typer av varningar:'''
exl-id: 707e20e0-faba-4bcd-884c-b54568787442
feature: Cache, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Hanterade aviseringar om Adobe Commerce: MariaDB-aviseringar

I den här artikeln beskrivs felsökningssteg när du får MariaDB-aviseringar för Adobe Commerce i New Relic. MariaDB-varningarna övervakar hög frågebelastning och överdrivna DML-frågor (Data Manipulation Language). Båda kan leda till en försämrad användarupplevelse eller till och med till driftstopp. Du kan få fyra typer av meddelanden:

* Varning för DML-frågor
* Kritiska DML-frågor

## **Berörda produkter och versioner**

Adobe Commerce om molninfrastruktur Pro planarkitektur

## Problem

Du får en hanterad avisering i New Relic om du har registrerat upp till [Hanterade aviseringar för Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) och ett eller flera av aviseringströskelvärdena har överskridits. Dessa varningar utvecklades av Adobe för att ge kunderna en standarduppsättning med hjälp av insikter från support och konstruktion.

**Gör!**

* Avbryt all schemalagd distribution tills den här aviseringen har rensats.
* Placera platsen i underhållsläge omedelbart om platsen inte svarar eller inte svarar alls. Anvisningar om hur du gör detta finns i [Installationshandbok > Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i utvecklardokumentationen. Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Anvisningar finns i [Underhåll listan över undantagna IP-adresser](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt).
* Avsluta alla skript, t.ex. import, som kan vara orsaken till varningen om platsens prestanda påverkas.

**Gör inte!**

* Kör indexerare eller ytterligare kroner som kan orsaka ytterligare stress för MariaDB.
* Utför några större administrativa uppgifter (t.ex. Commerce Admin, import/export av data).
* Rensa cachen.

## Lösning

**DML-frågor (frågor som ändrar databasen med UPDATE, INSERT och DELETE)**

Om du får en varning om allvarliga DML-frågor startar du steg ett. Om du får ett varningsmeddelande om DML-frågor startar du steg två.

1. Kontrollera om Adobe Commerce supportanmälan finns. Anvisningar finns i vår kunskapsbas [Spåra dina supportärenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets). Supporten kan ha tagit emot en New Relic-tröskelvarning, skapat en biljett och börjat arbeta med problemet. Om det inte finns någon biljett skapar du en. Biljetten ska ha följande information:
1. Kontaktorsak: välj&quot;New Relic MariaDB-avisering mottagen&quot;.
1. Beskrivning av aviseringen.
1. [Länk till New Relic Incident](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Detta ingår i dina [hanterade aviseringar för Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Identifiera orsaken till problemet genom att identifiera DML-frågorna:
1. Granska databasåtgärderna genom att använda steg från New Relic [API-gränssnittssidor > Övervakning > Databassida](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time) .
1. Sortera efter RÄKNA ANTAL och ÅTGÄRD. Granska INSERT-, DELETE- och UPDATE-åtgärder.
1. Håll utkik efter AVG.
1. Klicka igenom för att hitta anropare för databasåtgärder. Detta identifierar transaktioner som använder den frågan efter tid.
1. Se antingen kodoptimeringar eller operativa optimeringar:
1. Kodoptimeringar: Optimera frågor med massinfogningar/uppdateringar, minimera indexanvändning eller begränsa kod.
1. Operativa optimeringar: Avlasta resurskrävande dataändringar till lägre trafiktider.
1. Ytterligare optimeringar: Se till att du har den senaste versionen av ECE-Tools. Anvisningar om hur du gör detta finns i [Cloud för Adobe Commerce > Uppdatera versionen för verktygen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package) i utvecklardokumentationen.

## Relaterad läsning

* Om du vill undersöka andra vanliga MariaDB-problem kan du läsa [De vanligaste databasproblemen för Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html).
* Om du vill undersöka databasens bästa praxis kan du läsa [Databasgod praxis för Adobe Commerce om molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html).
