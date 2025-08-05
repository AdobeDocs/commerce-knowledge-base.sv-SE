---
title: 'Säkerhetskopiering (ögonblicksbild) i molnet: Vanliga frågor och svar'
description: I den här artikeln beskrivs grunderna för säkerhetskopiering av miljöer med ögonblicksbilder av Adobe Commerce om molninfrastruktur.
exl-id: 0077db74-3e7e-4c98-b215-7f6c089f49e8
feature: Cloud, Iaas
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '706'
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
* Automatiska ögonblicksbilder skapas **oavsett webbplatsens aktiva läge** (ögonblicksbilder skapas också för webbplatser som inte har startats ännu). Automatiska säkerhetskopior är inte tillgängliga för allmänheten eftersom de lagras i ett separat system.
Du kan [skicka en Adobe Commerce Support-biljett](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) för att begära en särskild säkerhetskopia eller för att återställa från en viss säkerhetskopia med datum, tid och tidszon i biljetten. När infrastrukturteamet har tillhandahållit ögonblicksbilden kör du följande kommando från den plats där ögonblicksbilden har placerats för att fastställa tidsstämpeln när den ursprungligen togs:

  `cat /mnt/recovery/vol-<volume_id>/snap.time`

  Exempelutdata:

  <strong>2025-01-13 08:42:17.123000+00:00</strong>


* Supporten genererar inga manuella ögonblicksbilder vid behov. Observera också att stödet inte utför återställning eller återställning av databasen åt dig. De hämtar ögonblicksbilden, men du måste återställa databasen själv.
* Automatiska ögonblicksbilder skapas **oavsett webbplatsens aktiva läge** (ögonblicksbilder skapas också för webbplatser som inte har startats ännu). Automatiska säkerhetskopior lagras i ett separat system och är inte tillgängliga för allmänheten.
Du kan [skicka en Adobe Commerce Support-biljett](/help/help-center-guide/help-center/magento-help-center-user-guide.md) för att begära en särskild säkerhetskopia eller för att återställa från en viss säkerhetskopia med datum, tid och tidszon i biljetten. Supporten genererar inga manuella ögonblicksbilder vid behov.
Observera också att stödet inte utför återställning eller återställning av databasen åt dig. De hämtar ögonblicksbilden, men du måste återställa databasen själv.
* Säkerhetskopiorna skapas med **krypterade ögonblicksbilder av Amazon Web Services Elastic Block Store (AWS EBS)**.
* Miljöögonblicksbilder innehåller hela systemet (filsystemet och databasen).
* Bevarandetiden för automatiska ögonblicksbilder **skiljer sig åt** och följer [schemat](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/pro-architecture#backup-and-disaster-recovery).

>[!NOTE]
>
>Molnkonsolen visar alltid [!UICONTROL No backup] i mellanlagrings- och produktionsmiljöer. Du kan bara ta säkerhetskopior från integreringsmiljön. Välj **[!UICONTROL Backup]** i listrutan Ellips.
>
>![cloud_console_backup.png](assets/cloud_console_backup.png)

### Integrationsmiljö (utveckling)

* [Integreringsmiljön](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242) säkerhetskopieras **inte automatiskt**, men du kan skapa ögonblicksbilder **manuellt**.
* Du kan skapa manuella ögonblicksbilder för integreringsmiljöer på butiker som inte är aktiva.
* Du kan ha **flera ögonblicksbilder** som har utlösts manuellt.
* En ögonblicksbild som aktiveras manuellt lagras i **7 dagar**.

**Relaterade artiklar i utvecklardokumentationen:**

* [Säkerhetskopiering och katastrofåterställning](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/pro-architecture#backup-and-disaster-recovery)
* [Skapa en ögonblicksbild](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/storage/snapshots)

## Miljöögonblicksbild, Starter-plan

* Alla typer av miljöer (integrering, mellanlagring, produktion) **säkerhetskopieras inte automatiskt**, men du kan skapa ögonblicksbilder manuellt.
* Du kan skapa manuella ögonblicksbilder **oavsett webbplatsens aktiva läge** (ögonblicksbilder skapas även för webbplatser som inte har startats ännu).
* En ögonblicksbild som aktiveras manuellt lagras i **7 dagar**.

## Återställ en ögonblicksbild av miljön

Om du vill återställa en befintlig ögonblicksbild (i den miljö som stöds: integrering, mellanlagring, produktion på startplan eller integrering på Pro-plan) följer du stegen i [Säkerhetskopieringshantering: Återställ en manuell säkerhetskopia](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup) i vår Commerce on Cloud Infrastructure Guide.

## Säkerhetskopiering av databas (DB)

Databassäkerhetskopiering är en del av en molnögonblicksbild:

En ögonblicksbild är en fullständig säkerhetskopia av en miljö som innehåller alla beständiga data från alla tjänster som körs (till exempel **din MySQL-databas**, Redis och så vidare) och alla filer som lagras på de monterade volymerna.

>[!NOTE]
>
>De monterade volymerna innehåller/refererar endast till [skrivbara monteringar](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/properties/properties#mounts) och kommer inte att innehålla hela din `/app`-katalog. Liksom för de andra filerna skapas/skapas de av [bygg- och distributionsprocessen](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/pro-develop-deploy-workflow#deployment-workflow), och du måste även checka ut de återstående filerna från Git-databasen.

[Ögonblicksbilder och hantering av säkerhetskopiering](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/storage/snapshots) i utvecklardokumentationen.

Skicka bara en [supportförfrågan](/help/help-center-guide/help-center/magento-help-center-user-guide.md) för en DB-ögonblicksbild från Pro Production och Staging om du behöver databasen från en viss tidpunkt. Om du bara behöver en aktuell säkerhetskopia av din databas (i vilken miljö som helst) kan du läsa artikeln i kunskapsbasen: [Generera databasdumpar i molnet](/help/how-to/general/create-database-dump-on-cloud.md).
