---
title: MySQL-flaskhalsar med hög belastning i Adobe Commerce i molninfrastruktur
description: I det här avsnittet diskuteras en lösning när hög belastning från MySQL orsakar ett problem med prestandaflaskhalsar i Adobe Commerce om molninfrastruktur.
exl-id: c1f9d282-41d8-4850-8a24-336d55aa3140
feature: Cloud, Observability, Paas, Services
role: Developer
source-git-commit: 075f55b94202f75839abd25bd47824eeb5226485
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---

# MySQL-flaskhalsar med hög belastning i Adobe Commerce i molninfrastruktur

I det här avsnittet diskuteras en lösning när hög belastning från MySQL orsakar ett problem med prestandaflaskhalsar i Adobe Commerce om molninfrastruktur.

## Berörda produkter och versioner

* Adobe Commerce on cloud infrastructure 2.x.x, Pro accounts.

### Förutsättningar

* ECE-verktyg version 2002.0.16 och senare
* New Relic APM-tjänst (**Ditt Adobe Commerce-konto för molninfrastruktur innehåller programvaran för New Relic APM-tjänst** tillsammans med en licensnyckel.)

Mer information om New Relic APM-tjänsten och dess konfiguration med ditt Adobe Commerce på molninfrastrukturkontot finns på [New Relic Services](https://devdocs.magento.com/guides/v2.3/cloud/project/new-relic.html) och [Introduktion till New Relic APM](https://docs.newrelic.com/docs/apm/new-relic-apm/getting-started/introduction-apm/).

## Problem

<u>Steg för att se om problemet påverkar dig</u>

1. I översiktsdiagrammet för New Relic APM ska du kontrollera den första indikationen på att MySQL har blivit en flaskhals. Se exempelbilden nedan där MySQL har blivit en flaskhals och tar större delen av webbtransaktionstiden:

   ![KB-372_image002.png](assets/KB-372_image002.png)

   Lägg märke till hur den röda streckade linjen i bilden visar en märkbar uppåtgående trend i MySQL-webbtransaktionerna och sedan toppar på ännu högre nivåer.
1. Härifrån kan du sedan gå till **Databas** skärm där du kan se den andra indikationen på hög genomströmning eller långsam `SELECT` frågor i MySQL och i exempelbilden nedan kan du se när du sorterar efter **Den mest tidskrävande**&#x200B;är butiken i det här exemplet långsam på `SELECT` MySQL-frågor.

   ![KB-372_image003_BludadExtension.png](assets/KB-372_image003_BlurredExtension.png)

Analysera långsamma transaktioner i New Relic APM. Om du ser ett stort antal frågor eller ett högt tryck på en MySQL-databas kan du sprida belastningen över olika noder genom att aktivera `SLAVE` anslutningar.

## Orsak

Din Adobe Commerce-butik i molnet har hög genomströmning eller är långsam på `SELECT` MySQL-frågor.

## Lösning

>[!WARNING]
>
>För skalad arkitektur (delad arkitektur), Redis-slavanslutningar **FÅR INTE** aktiveras. Du kan kontrollera om du har en skalad arkitektur genom att gå till projekt-URL:en, t.ex. `https://console.adobecommerce.com/<owner-user-name>/<project-ID>/<environment-name>`. Klicka på **[!UICONTROL SSH]**. Om det finns fler än tre noder är du i en skalad arkitektur. Om du aktiverar Redis Slave Reads för skalad arkitektur får kunden felmeddelanden om att Redis-anslutningar inte kan ansluta. Detta har att göra med hur klustren har konfigurerats för att bearbeta Redis-anslutningar. Redis Slaves är fortfarande aktivt men kommer inte att användas för Redis-läsningar. Vi rekommenderar att den skalade arkitekturen använder Adobe Commerce 2.3.5 eller senare och implementerar den nya Redis back-end-konfigurationen och implementerar L2-cachning för Redis.

Om de upplever dessa två indikationer, `SLAVE` anslutningar för MySQL-databasen och Redis kan bidra till att sprida ut belastningen över olika noder.

Adobe Commerce kan läsa flera databaser eller Redis asynkront. Uppdaterar `.magento.env.yaml` fil genom att ange `true` värdena `MYSQL_USE_SLAVE_CONNECTION` och `REDIS_USE_SLAVE_CONNECTION` för att använda **skrivskyddad** anslutning till databasen för att ta emot skrivskyddad trafik på en icke-huvudnod. Detta förbättrar prestanda genom lastbalansering eftersom bara en nod behöver hantera trafik med läs- och skrivbehörighet. Ange till `false` om du vill ta bort en befintlig skrivskyddad anslutningsmatris från `env.php` -fil.

### Steg

1. Redigera dina `.magento.env.yaml` och lägga till följande innehåll:

   ![KB-372_image004.png](assets/KB-372_image004.png)

   Mer information finns i [Distribuera variabler i DevDocs](https://devdocs.magento.com/cloud/env/variables-deploy.html#mysql_use_slave_connection).

1. Genomför ändringarna och gör ändringarna mer omfattande.
1. När du gör ändringar initieras en ny distributionsprocess. När distributionen är klar bör du nu ha konfigurerat Adobe Commerce på molninfrastrukturinstansen så att den använder slavanslutningar.

## Vanliga frågor

Nedan beskrivs de vanligaste frågorna du kan ställa när du funderar på att använda Slave Connections-funktionen för din Adobe Commerce i molninfrastrukturbutiken.

* Finns det några kända problem eller begränsningar för att använda slavanslutningar? **Vi har inga kända problem med att använda slavanslutningar. Se bara till att du använder det senaste uppdaterade verktygspaketet. Instruktioner finns här [hur du uppdaterar verktygspaketet](https://devdocs.magento.com/cloud/project/ece-tools-update.html).**
* Finns det någon extra fördröjning genom att använda slavanslutningar? *Ja, fördröjningen mellan AZ (cross-Availability Zones) är högre och minskar prestandan för en Adobe Commerce på en molninfrastrukturinstans om instansen inte är överbelastad och kan bära hela belastningen. Men om instansen är överlastad är det tydligt att masterslave hjälper till med prestandan genom att sprida belastningen på MySQL-databasen eller Redis över olika noder.*

  **Vid kluster som inte är överbelastade** -  **Slave Connections sänker prestanda med 10-15 %**, vilket är en av anledningarna till att det inte är standard.

  *Men i överbelastade kluster ökar prestandan eftersom dessa 10-15 % minskas genom att belastningen minskas med trafiken.*
* Ska jag aktivera de här inställningarna för min butik? *Om du har hög belastning eller förväntar dig hög belastning på MySQL-databasen eller Redis måste du definitivt aktivera slavanslutningar. För en kund med normal trafik är detta **not**en optimal inställning som ska aktiveras.*

## Relaterad läsning

I vår utvecklardokumentation:

* [Distribuera variabler](https://devdocs.magento.com/cloud/env/variables-deploy.html).
* [Ställ in valfri databasreplikering](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master_slavedb.html).
* [hjälpmedelspaket](https://devdocs.magento.com/cloud/reference/ece-tools-reference.html).

>[!NOTE]
>
>Vi är medvetna om att den här artikeln fortfarande kan innehålla programtermer som är branschstandard och som vissa kan finna rasistiska, sexistiska eller förtryckande, och som kan få läsaren att känna sig sårad, traumatiserad eller ovälkommen. Adobe arbetar med att ta bort dessa villkor från vår kod, dokumentation och användarupplevelse.
