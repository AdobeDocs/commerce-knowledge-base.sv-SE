---
title: 'Säkerhetskopiera (ögonblicksbild) i molnet: Vanliga frågor'
description: I den här artikeln beskrivs grunderna för säkerhetskopiering av miljöer med ögonblicksbilder av Adobe Commerce om molninfrastruktur.
exl-id: 0077db74-3e7e-4c98-b215-7f6c089f49e8
feature: Cloud, Iaas
source-git-commit: 0958a8923e27c1341f4b536812b26205685b2b81
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# Säkerhetskopiering (ögonblicksbild) i molnet: Vanliga frågor och svar

I den här artikeln beskrivs hur du säkerhetskopierar miljöer med ögonblicksbilder av Adobe Commerce om molninfrastruktur.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur 2.4.x
* Arkitektursplaner: Starter, Pro Legacy, Pro

## Miljöögonblicksbild, Pro-plan

### Mellanlagrings- och produktionsmiljöer

* Manuella ögonblicksbilder är inte tillgängliga för miljöer med mellanlagring och produktion i Pro-planen.
* Automatiska ögonblicksbilder skapas **oavsett Live-läge** av din webbplats (ögonblicksbilder skapas också för webbplatser som ännu inte har startats). Automatiska säkerhetskopior är inte tillgängliga för allmänheten eftersom de lagras i ett separat system. Du kan [skicka en Adobe Commerce-supportanmälan](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) för att begära en särskild säkerhetskopia eller för att återställa från en viss säkerhetskopia med datum, tid och tidszon i biljetten. Observera också att stödet inte utför återställning eller återställning av databasen åt dig. De hämtar ögonblicksbilden, men du måste återställa databasen själv.
* Säkerhetskopiorna skapas med **krypterade ögonblicksbilder av Amazon Web Services Elastic Block Store (AWS EBS)**.
* Miljöögonblicksbilder innehåller hela systemet (filsystemet och databasen).
* Bevarandetid för automatiska ögonblicksbilder **är annorlunda** och följande [schemat](/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html?lang=en#backup-and-disaster-recovery).

>[!NOTE]
>Molnkonsolen visas alltid [!UICONTROL No backup] i mellanlagrings- och produktionsmiljöer. Du kan bara ta säkerhetskopior från integreringsmiljön. Välj **[!UICONTROL Backup]** på den nedrullningsbara ellipsmenyn.
>![cloud_console_backup.png](assets/cloud_console_backup.png)





### Integrationsmiljö (utveckling)

* Dina [Integreringsmiljö](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) är **inte säkerhetskopieras automatiskt** men du kan skapa fixeringar **manuellt**.
* Du kan skapa manuella ögonblicksbilder för integreringsmiljöer på butiker som inte är aktiva.
* Du kanske har **flera ögonblicksbilder** som har utlösts manuellt.
* En ögonblicksbild som aktiveras manuellt sparas för **7 dagar**.

**Relaterade artiklar i vår utvecklardokumentation:**

* [Säkerhetskopiering och katastrofåterställning](/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#backup-and-disaster-recovery)
* [Skapa en fixering](/docs/commerce-cloud-service/user-guide/develop/storage/snapshots.html)

## Miljöögonblicksbild, Starter-plan

* Alla typer av miljöer (integrering, mellanlagring, produktion) **säkerhetskopieras inte automatiskt** men du kan skapa ögonblicksbilder manuellt.
* Du kan skapa manuella ögonblicksbilder **oavsett Live-läge** av din webbplats (ögonblicksbilder skapas också för webbplatser som ännu inte har startats).
* En ögonblicksbild som aktiveras manuellt sparas för **7 dagar**.

## Återställ en ögonblicksbild av miljön

Om du vill återställa en befintlig ögonblicksbild (i den miljö som stöds: Integration, Mellanlagring, Produktion på Starter-plan eller Integrering på Pro-plan) följer du stegen i [Hantering av säkerhetskopiering: Återställ en manuell säkerhetskopiering](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup) i vår Commerce on Cloud Infrastructure Guide.

## Säkerhetskopiering av databas (DB)

Databassäkerhetskopiering är en del av en molnögonblicksbild:

>>
En ögonblicksbild är en fullständig säkerhetskopia av en miljö som innehåller alla beständiga data från alla tjänster som körs (till exempel **din MySQL-databas**, Redis och så vidare) och alla filer som lagras på de monterade volymerna.

>[!NOTE]
>
>De monterade volymerna innehåller/refererar endast till [skrivbar montering](/docs/commerce-cloud-service/user-guide/configure/app/properties/properties.html?lang=en#mounts) och kommer inte att innehålla hela din /app-katalog. De andra filerna skapas/skapas av [bygg- och distributionsprocessen](/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=en#deployment-workflow)och du måste även checka ut de återstående filerna från din Git-databas.

[Ögonblicksbilder och hantering av säkerhetskopiering](/docs/commerce-cloud-service/user-guide/develop/storage/snapshots.html) i vår dokumentation för utvecklare.

Skicka endast [supportförfrågan](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) för en DB-ögonblicksbild från Pro Production och Staging om du behöver databasen från en viss tidpunkt. Om du behöver en aktuell säkerhetskopia av din databas (endast i en viss miljö) kan du läsa artikeln i kunskapsbasen: [Generera databasdumpar i molnet](/help/how-to/general/create-database-dump-on-cloud.md).
