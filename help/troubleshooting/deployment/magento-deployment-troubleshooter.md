---
title: Adobe Commerce felsökare vid driftsättning
description: Stuckedistributioner och misslyckade distributioner på Adobe Commerce kan lösas med felsökningsverktyget för distribution. Klicka på varje fråga för att visa svaret i varje steg i felsökaren.
exl-id: 5141e079-be61-44c2-8bff-c4b13cb7e07c
feature: Build, Deploy, Support
role: Developer
source-git-commit: 4704446d043e3175b5af27c068908e58bfb7a9ff
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---

# Adobe Commerce felsökare vid driftsättning

Stuckedistributioner och misslyckade distributioner på Adobe Commerce kan lösas med felsökningsverktyget för distribution. Klicka på varje fråga för att visa svaret i varje steg i felsökaren.

## Steg 1 - Kontrollera att tjänsten körs {#step-1}

+++**Är Adobe Commerce i molninfrastrukturtjänsten tillgänglig?**

Driftsättning av Stuck - Är Adobe Commerce i molninfrastrukturtjänsten tillgänglig? Kontrollera [Adobe Commerce Cloud](https://status.adobe.com/products/3350/).

a. JA - Fortsätt till [Steg 2](#step-2).\
b. NO - Underhållsavbrott eller globala driftavbrott. Kontrollera om det finns beräknade varaktigheter och uppdateringar.

+++

## Steg 2 - Kontrollera distributioner i andra miljöer {#step-2}

+++**Finns det distributioner i andra miljöer som blockerar distributionen i den befintliga miljön?**

För att få en lista över pågående aktiviteter kör du följande kommando med magento-cloud CLI (om du bara har lagts till i ett molnprojekt). **Obs!** Kontrollera att du har den senaste versionen av magento-cloud CLI. Anvisningar finns i [Uppdatera CLI](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/cloud-cli/cloud-cli-overview) i guiden för Commerce om molninfrastruktur.

```bash
magento-cloud --state=in_progress
```

För att få en lista över pågående aktiviteter kör du följande kommando med magento-cloud CLI (om du har lagts till i flera projekt):

```bash
magento-cloud -p <project-id or project-url> --state=in_progress
```

Om du vill hitta information om en befintlig distributionsaktivitet (se [Kontrollera distributionsloggen om molngränssnittet har felet&quot;loggad&quot;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error))
om du vill ha mer information) kan du köra det här kommandot för att få en logg över aktiviteten:

```bash
magento-cloud activity:log <activity-id> [OPTIONAL: <-p project-id or project-url>]
```

a. JA - Felsök den andra miljön och blockera distributionen i den befintliga miljön. Fortsätt till [Steg 3](#step-3).

b. NEJ - Felsök den aktuella miljön. Fortsätt till [Steg 3](#step-3).

+++


## Steg 3 - Verifiera SSH på alla noder {#step-3}

+++**SSH lyckades för alla noder?**

a. JA - Fortsätt till [Steg 4](#step-4).\
b. NEJ - [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Steg 4 - Verifiera alla tjänster som körs {#step-4}

+++**Alla tjänster körs?**

a. JA - Fortsätt till [steg 5](#step-5).\
b. NEJ - [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Steg 5 - Verifiera att Bitbucket körs {#step-5}

+++**Använder du Bitbucket?**

a. JA - Kontrollera [status.bitbucket.com](https://bitbucket.status.atlassian.com/).\
b. NO - Kontrollera distributionsloggfel i [Build and Deploy logs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/log-locations). Fortsätt till [Steg 6](#step-6).

+++

## Steg 6 - Kontrollera felkoder {#step-6}

+++**Felkoden har rapporterats?**

a. JA - Fortsätt till [Steg 7](#step-7).\
b. NEJ - Fortsätt till [steg 8](#step-8).

+++

## Steg 7 - 403 Ej tillåtet fel {#step-7}

+++**403 Ej tillåtet?**

a. JA - Fortsätt till [steg 16](#step-16).
b. NEJ - Fortsätt till [steg 9](#step-9).

+++

## Steg 8 - Verifiera att cron-jobb körs {#step-8}

+++**Kör seriejobb just nu?** Logga in med ssh i förgreningen och kör `ps aufxx |grep cron`.

a. JA - Logga in med ssh på den berörda grenen (t.ex. primär). Dödar och låser upp cron-jobb. Detta kommer att avsluta cron-jobb och återställa statusen. Kör `php vendor/bin/ece-tools cron:kill` och sedan `php vendor/bin/ece-tools cron:unlock`. Om du håller på att sammanfoga en miljö till en annan bör du kontrollera om båda miljöerna har kroner som körs.\
b. NEJ - Fortsätt till [steg 17](#step-17).

+++

## Steg 9 - Program som kan distribueras till fjärrkluster-fel {#step-9}

+++**Kan inte överföra program till fjärrklustret?**

a. JA - Fortsätt till [steg 10](#step-10).\
b. NEJ - Fortsätt till [steg 11](#step-11).

+++

## Steg 10 - Kontrollera att lagringsutrymmet är tillräckligt {#step-10}

+++**Tillgänglig lagring fungerar?**

a. JA - Fortsätt med [steg 11](#step-11).\
b. NEJ - Granska [Hantera diskutrymme](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space).

+++

## Steg 11 - Verifiera diskutrymme {#step-11}

+++**_filen kunde inte skrivas med varning _?**

a. JA - Öka diskvärdet i .magento.app.yaml](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space) och återdistribuera. [ Om detta inte fungerar skickar [en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NEJ - Fortsätt med [steg 12](#step-12).

+++

## Steg 12 - Fel vid miljöomdistribution {#step-12}

+++**Omdistributionen av miljön misslyckades?**

a. JA - Fortsätt med [steg 13](#step-13).\
b. NEJ - Fortsätt med [steg 8](#step-8).

+++

## Steg 13 - Kontrollera om Elasticsearch uppgradering misslyckades {#step-13}

+++**Elasticsearch uppgraderas eller distribueras?**

a. JA - Elasticsearch misslyckades med uppgraderingsstegen. Se [Kompatibilitet med Elasticsearch-program](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html). Om Elasticsearch-uppgraderingen fortfarande inte fungerar kan du [skicka in en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). **Obs!** På Adobe Commerce i molninfrastruktur bör du vara medveten om att serviceuppgraderingar inte kan skickas till produktionsmiljön utan att meddela vårt infrastrukturteam om 48 arbetstimmar. Detta är nödvändigt eftersom vi måste se till att det finns en infrastruktursupporttekniker tillgänglig som kan uppdatera din konfiguration inom den önskade tidsramen med minimala driftavbrott i din produktionsmiljö. Så 48 timmar före när dina ändringar behöver vara i produktion skickar [en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) med information om den serviceuppgradering du behöver och när du vill att uppgraderingsprocessen ska börja.\
b. NEJ - Fortsätt till [steg 14](#step-14).

+++

## Steg 14 - Kontrollera utrymmesbegränsningar {#step-14}

+++**Filsystemet har slut på noder eller utrymme?**

a. JA - Se [Hantera diskutrymme](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space).\
b. NEJ - Fortsätt till [steg 15](#step-15).

+++

## Steg 15 - Elasticsearch-versionsfel {#step-15}

+++**Fel i Elasticesach-versioner?**

a. JA - Fortsätt till [steg 16](#step-16).\
b. NEJ - Fortsätt till [steg 21](#step-21).

+++

## Steg 16 - Verifiera konfiguration för disposition {#step-16}

+++**Konfigurationen för disposition är korrekt?**

a. JA - Fortsätt till [steg 10](#step-10).\
b. NEJ - Granska [webbsidan Felsökning för disposition](https://getcomposer.org/doc/articles/troubleshooting.md).

+++

## Steg 17 - Kontrollera om det finns långa processer {#step-17}

+++**Långa processer?**

a. JA - Identifiera långvariga processer och avsluta sedan processerna:
1. Kör följande kommando i terminalen: `ps aufx`.
1. Leta reda på PID för den långvariga processen.
1. Avsluta processen med `kill -9 <PID>`.

Övervaka distributioner för återkomst.

b. NEJ - Fortsätt till [steg 18](#step-18).

+++

## Steg 18 - Kontrollera om det inte gick att utföra en postkrok {#step-18}

+++**Efterbeställning av krokfel/hängande?**

a. JA - Databas: [Ledigt diskutrymme](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#allocate-disk-space), skadade, ofullständiga/skadade tabeller.\
b. NEJ - Fortsätt till [steg 19](#step-19).

+++

## Steg 19 - Kontrollera om tillägg från tredje part blockerar distribution {#step-19}

+++**Använda tillägg från tredje part?**

a. JA - Prova [Inaktivera tillägg från tredje part](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure-store/extensions) och kör distributionen (för att se om de är orsaken till problemet), särskilt om det finns tilläggsnamn i några fel.\
b. NEJ - Fortsätt till [steg 20](#step-20).

+++

## Steg 20 - Kontrollera om det finns långsamma frågor {#step-20}

+++**Långa frågor?**

[Kontrollera långsam frågelogg och MySQL-visningsprocesslista](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md).

a. JA - Avsluta alla långvariga frågor. Granska [MySQL-avslutningssyntax.](https://dev.mysql.com/doc/refman/8.0/en/kill.html)\
b. NEJ - [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Steg 21 - nedgradera Elasticsearch {#step-21}

+++**Vill du nedgradera Elasticsearch-versioner?**

a. JA - Kan inte göras via konfigurationen. [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NEJ - [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Tillbaka till steg 1](#step-1)
