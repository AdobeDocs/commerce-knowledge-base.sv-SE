---
title: Adobe Commerce felsökare vid driftsättning
description: Stuckedistributioner och misslyckade distributioner på Adobe Commerce kan lösas med felsökningsverktyget för distribution. Klicka på varje fråga för att visa svaret i varje steg i felsökaren.
exl-id: 5141e079-be61-44c2-8bff-c4b13cb7e07c
feature: Build, Deploy, Support
role: Developer
source-git-commit: 6177863da268f43cc30119cef6f718a04c46b3e6
workflow-type: tm+mt
source-wordcount: '933'
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

För att få en lista över pågående aktiviteter kör du följande kommando med magento-cloud CLI (om du bara har lagts till i ett molnprojekt):

```bash
magento-cloud --state=in_progress
```

För att få en lista över pågående aktiviteter kör du följande kommando med magento-cloud CLI (om du har lagts till i flera projekt):

```bash
magento-cloud -p <project-id or project-url> --state=in_progress
```

Information om en befintlig distributionsaktivitet finns i [Kontrollerar distributionsloggen om molnanvändargränssnittet har fel av typen&quot;loggutdragen&quot;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error.html)
om du vill ha mer information) kan du köra det här kommandot för att få en logg över aktiviteten:

```bash
magento-cloud activity:log <activity-id> [OPTIONAL: <-p project-id or project-url>]
```

a. JA - Felsök den andra miljön och blockera distributionen i den befintliga miljön. Fortsätt till [Steg 3](#step-3).

b. NEJ - Felsök den aktuella miljön. Fortsätt till [Steg 3](#step-3).

+++


## Steg 3 - Verifiera SSH på alla noder {#step-3}

+++**SSH lyckades på alla noder?**

a. JA - Fortsätt till [Steg 4](#step-4).\
b. NEJ - [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Steg 4 - Verifiera alla tjänster som körs {#step-4}

+++**Alla tjänster som körs?**

a. JA - Fortsätt till [Steg 5](#step-5).\
b. NEJ - [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Steg 5 - Verifiera att Bitbucket körs {#step-5}

+++**Använder du Bitbucket?**

a. JA - Kontrollera [status.bitbucket.com](https://bitbucket.status.atlassian.com/).\
b. NO - Kontrollera distributionsloggfel i [Skapa och distribuera loggar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html). Fortsätt till [Steg 6](#step-6).

+++

## Steg 6 - Kontrollera felkoder {#step-6}

+++**Felkod rapporterad?**

a. JA - Fortsätt till [Steg 7](#step-7).\
b. NEJ - Fortsätt till [Steg 8](#step-8).

+++

## Steg 7 - 403 Ej tillåtet fel {#step-7}

+++**403 Förbjuden?**

a. JA - Fortsätt till [Steg 16](#step-16).
b. NEJ - Fortsätt till [Steg 9](#step-9).

+++

## Steg 8 - Verifiera att cron-jobb körs {#step-8}

+++**Körs cron-jobb just nu?** Logga in med ssh på grenen och kör `ps aufxx |grep cron`.

a. JA - Logga in med ssh på den berörda grenen (t.ex. primär). Dödar och låser upp cron-jobb. Detta kommer att avsluta cron-jobb och återställa statusen. Kör `php vendor/bin/ece-tools cron:kill` och sedan `php vendor/bin/ece-tools cron:unlock`. Om du håller på att sammanfoga en miljö till en annan bör du kontrollera om båda miljöerna har kroner som körs.\
b. NEJ - Fortsätt till [Steg 17](#step-17).

+++

## Steg 9 - Program som kan distribueras till fjärrkluster-fel {#step-9}

+++**Kan du inte överföra programmet till fjärrklusterfelet?**

a. JA - Fortsätt till [Steg 10](#step-10).\
b. NEJ - Fortsätt till [Steg 11](#step-11).

+++

## Steg 10 - Kontrollera att lagringsutrymmet är tillräckligt {#step-10}

+++**Tillgänglig lagring är okej?**

a. JA - Fortsätt med [Steg 11](#step-11).\
b. NEJ - Granska [Hantera diskutrymme](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html).

+++

## Steg 11 - Verifiera diskutrymme {#step-11}

+++**_filen kunde inte skrivas Varning _?**

a. JA - Vänligen [öka diskvärdet i .magento.app.yaml](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space) och omdistribuera. Om det inte fungerar [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NEJ - Fortsätt med [Steg 12](#step-12).

+++

## Steg 12 - Fel vid miljöomdistribution {#step-12}

+++**Fel vid miljöomdistribution?**

a. JA - Fortsätt med [Steg 13](#step-13).\
b. NEJ - Fortsätt med [Steg 8](#step-8).

+++

## Steg 13 - Kontrollera om Elasticsearch-uppgradering misslyckades {#step-13}

+++**Elasticsearch håller på att uppgraderas eller driftsättas?**

a. JA - Elasticsearch misslyckades med uppgraderingsstegen. Se [Kompatibilitet med Elasticsearch-program](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html). Om uppgraderingen av Elasticsearch fortfarande inte fungerar, [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). **Anteckning**: På Adobe Commerce i molninfrastruktur bör du vara medveten om att serviceuppgraderingar inte kan föras över till produktionsmiljön utan att vårt infrastrukturteam får ett meddelande om detta inom 48 timmar. Detta är nödvändigt eftersom vi måste se till att det finns en infrastruktursupporttekniker tillgänglig som kan uppdatera din konfiguration inom den önskade tidsramen med minimala driftavbrott i din produktionsmiljö. Så 48 timmar före när ändringarna ska vara i produktion, [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) ange vilken serviceuppgradering du behöver och ange när du vill att uppgraderingen ska starta.\
b. NEJ - Fortsätt till [Steg 14](#step-14).

+++

## Steg 14 - Kontrollera utrymmesbegränsningar {#step-14}

+++**Har filsystemet slut på noder eller utrymme?**

a. JA - Se [Hantera diskutrymme](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space).\
b. NEJ - Fortsätt till [Steg 15](#step-15).

+++

## Steg 15 - Elasticsearch-versionsfel {#step-15}

+++**Fel med Elasticesach-versioner?**

a. JA - Fortsätt till [Steg 16](#step-16).\
b. NEJ - Fortsätt till [Steg 21](#step-21).

+++

## Steg 16 - Verifiera konfiguration för disposition {#step-16}

+++**Konfigurationen av dispositionen är korrekt?**

a. JA - Fortsätt till [Steg 10](#step-10).\
b. NEJ - Granska [Webbsida för felsökare för disposition](https://getcomposer.org/doc/articles/troubleshooting.md).

+++

## Steg 17 - Kontrollera om det finns långa processer {#step-17}

+++**Långa processer?**

a. JA - Identifiera långvariga processer och avsluta sedan processerna:
1. Kör följande kommando i terminalen: `ps aufx`.
1. Leta reda på PID för den långvariga processen.
1. Avsluta processen med `kill -9 <PID>`.

Övervaka distributioner för återkomst.

b. NEJ - Fortsätt till [Steg 18](#step-18).

+++

## Steg 18 - Kontrollera om det inte gick att utföra en postkrok {#step-18}

+++**Har du inte fastnat?**

a. JA - Databas: [Ledigt diskutrymme](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#allocate-disk-space), skadade, ofullständiga/skadade tabeller.\
b. NEJ - Fortsätt till [Steg 19](#step-19).

+++

## Steg 19 - Kontrollera om tillägg från tredje part blockerar distribution {#step-19}

+++**Använda tillägg från tredje part?**

a. JA - Prova [Inaktivera tillägg från tredje part](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html) och köra distributionen (för att se om det är orsaken till problemet), särskilt om det finns tilläggsnamn i några fel.\
b. NEJ - Fortsätt till [Steg 20](#step-20).

+++

## Steg 20 - Kontrollera om det finns långsamma frågor {#step-20}

+++**Långa frågor?**

[Kontrollera långsam frågelogg och MinSQL-visningsprocesslista](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md).

a. JA - Avsluta alla långvariga frågor. Granska [MySQL Kill Syntax.](https://dev.mysql.com/doc/refman/8.0/en/kill.html)\
b. NEJ - [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Steg 21 - nedgradera Elasticsearch {#step-21}

+++**Vill du nedgradera Elasticsearch versioner?**

a. JA - Kan inte göras via konfigurationen. [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NEJ - [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Tillbaka till steg 1](#step-1)
