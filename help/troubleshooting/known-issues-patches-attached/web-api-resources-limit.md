---
title: Webb-API:t kan inte bearbeta begäranden med mer än 20 objekt i matrisen
description: Den här artikeln innehåller en lösning på problemet där webb-API inte kan bearbeta ett meddelande som innehåller mer än 20 objekt i arrayen för Adobe Commerce 2.4.3.
exl-id: 7e6b3fe8-3133-4773-afa7-fbfdd98ecde9
feature: REST
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Webb-API:t kan inte bearbeta begäranden med mer än 20 objekt i matrisen

Den här artikeln innehåller en lösning på problemet där webb-API inte kan bearbeta ett meddelande som innehåller mer än 20 objekt i arrayen för Adobe Commerce 2.4.3.

## Berörda produkter och versioner:

* Adobe Commerce (alla distributionsmetoder) 2.4.3 och 2.3.7-p1
* Magento Open Source 2.4.3 och 2.3.7-p1

## Problem

Det går inte att bearbeta meddelandet (till exempel Stock Update) som innehåller mer än 20 objekt i arrayen.

## Orsak

I Adobe Commerce 2.4.3 lades den inbyggda hastighetsbegränsningen till Magento API:er för att förhindra DoS-attacker (denial of service).

Som standard är följande inbyggda API-hastighetsbegränsning tillgänglig:

* REST-begäranden som innehåller indata som representerar en lista över enheter är begränsade till högst 20 standardenheter
* REST- och GraphQL-frågor som tillåter sidnumrerade resultat är begränsade till standardvärdet 300 objekt per sida

## Lösning

Om du vill inaktivera indatagränserna för REST API-begäran använder du någon av följande patchar (beroende på version):

* [MC-43048__set_rate_limits__2.3.7-p1.patch.zip](assets/MC-43048__set_rate_limits__2.3.7-p1.patch.zip)
* [MC-43048__set_rate_limits__2.4.3.patch.zip](assets/MC-43048__set_rate_limits__2.4.3.patch.zip)

### Kompatibla Adobe Commerce-versioner

Patcharna skapades för:

* Adobe Commerce om molninfrastruktur 2.4.3 och 2.3.7-p1
* Adobe Commerce lokal 2.4.3 och 2.3.7-p1

Patcherna är inte kompatibla med andra Adobe Commerce-versioner.

### Så här sätter du på plåstret

Zippa upp det nedladdade `.zip` och tillämpa korrigeringen enligt beskrivningen i [Använda en kompositkorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

>[!WARNING]
>
>Om du misstänker att butik drabbas av en DoS-attack rekommenderar Adobe att standardindatagränserna sänks till ett lägre värde för att begränsa antalet resurser som kan begäras.  Du kan anpassa standardgränserna programmatiskt med [klasskonstruktorargument](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html)
>enligt beskrivningen i vår utvecklardokumentation: [API-säkerhet > Hastighetsbegränsning > Maximalt antal parameterindata](https://devdocs.magento.com/guides/v2.4/get-started/api-security.html#rate-limiting).

## Relaterad läsning

[API-säkerhet > Hastighetsbegränsning](https://devdocs.magento.com/guides/v2.4/get-started/api-security.html#rate-limiting) i vår dokumentation för utvecklare.
