---
title: 'Hanterade aviseringar om Adobe Commerce: MariaDB-aviseringar'
description: '"I den här artikeln beskrivs felsökningssteg när du får MariaDB-aviseringar för Adobe Commerce i New Relic. MariaDB-varningarna övervakar hög frågebelastning och överdrivna DML-frågor (Data Manipulation Language). Båda kan leda till en försämrad användarupplevelse eller till och med till driftstopp. Du kan få fyra typer av varningar:'''
exl-id: 707e20e0-faba-4bcd-884c-b54568787442
feature: Cache, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
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

Du får en hanterad avisering i New Relic om du har registrerat dig för [Hanterade aviseringar för Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) och ett eller flera av tröskelvärdena för larm har överskridits. Dessa varningar utvecklades av Adobe för att ge kunderna en standarduppsättning med hjälp av insikter från support och konstruktion.

**Gör!**

* Avbryt all schemalagd distribution tills den här aviseringen har rensats.
* Placera platsen i underhållsläge omedelbart om platsen inte svarar eller inte svarar alls. För steg se [Installationsguide > Aktivera eller inaktivera underhållsläge](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) i vår dokumentation för utvecklare. Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Om du vill se steg går du till [Underhåll listan över undantagna IP-adresser](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt).
* Avsluta alla skript, t.ex. import, som kan vara orsaken till varningen om platsens prestanda påverkas.

**Gör det inte!**

* Kör indexerare eller ytterligare kroner som kan orsaka ytterligare stress för MariaDB.
* Utför några större administrativa uppgifter (t.ex. Commerce Admin, import/export av data).
* Rensa cachen.

## Lösning

**DML-frågor (frågor som ändrar databasen med UPDATE, INSERT och DELETE)**

Om du får en varning om allvarliga DML-frågor startar du steg ett. Om du får ett varningsmeddelande om DML-frågor startar du steg två.

1. Kontrollera om Adobe Commerce supportanmälan finns. Anvisningar finns i vår kunskapsbas [Spåra era supportärenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets). Supporten kan ha tagit emot en New Relic-tröskelvarning, skapat en biljett och börjat arbeta med problemet. Om det inte finns någon biljett skapar du en. Biljetten ska ha följande information:
1. Kontaktorsak: välj&quot;New Relic MariaDB-avisering mottagen&quot;.
1. Beskrivning av aviseringen.
1. [Länk till New Relic Incident](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Detta ingår i [Hanterade aviseringar för Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Identifiera orsaken till problemet genom att identifiera DML-frågorna:
1. Granska databasåtgärderna genom att använda steg från New Relic [APM UI Pages > Monitoring > Databases page](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time) .
1. Sortera efter RÄKNA ANTAL och ÅTGÄRD. Granska INSERT-, DELETE- och UPDATE-åtgärder.
1. Håll utkik efter AVG.
1. Klicka igenom för att hitta anropare för databasåtgärder. Detta identifierar transaktioner som använder den frågan efter tid.
1. Se antingen kodoptimeringar eller operativa optimeringar:
1. Kodoptimeringar: Optimera frågor med massinfogningar/uppdateringar, minimera indexanvändning eller begränsa kod.
1. Operativa optimeringar: Avlasta resurskrävande dataändringar till lägre trafiktider.
1. Ytterligare optimeringar: Se till att du har den senaste versionen av ECE-Tools. Om du vill se steg går du till [Cloud för Adobe Commerce > Uppdatera skolverktygets version](https://devdocs.magento.com/cloud/project/ece-tools-update.html) i vår dokumentation för utvecklare.

## Relaterad läsning

* Om du vill undersöka andra vanliga MariaDB-problem kan du läsa [De vanligaste databasproblemen för Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html).
* Bästa tillvägagångssätt för att söka efter databaser finns i [Bästa databaspraxis för Adobe Commerce om molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html).
