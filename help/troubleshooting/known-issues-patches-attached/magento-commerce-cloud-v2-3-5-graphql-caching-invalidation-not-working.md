---
title: Adobe Commerce on cloud infrastructure v2.3.5 GraphQL caching invalidisation fungerar inte
description: Den här artikeln innehåller en korrigeringsfil för problemet där GraphQL "GET" begär inaktuell information om kunden ändrar produktinformationen.
exl-id: 10ae52bd-e71a-42e3-9600-7a9713903815
feature: GraphQL, Cache, Categories, Cloud, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Adobe Commerce on cloud infrastructure v2.3.5 GraphQL caching invalidisation fungerar inte

Den här artikeln innehåller en korrigeringsfil för problemet där GraphQL `GET` begär att få tillbaka föråldrad information om kunden ändrar produktinformationen.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur v2.3.5.

## Problem

GraphQL-begäranden cachelagras av Fastly och den cachelagrade versionen hämtas för varje efterföljande begäran från Fastly. När en produkt sparas på nytt i Adobe Commerce serverdel, bör snabbcachen ogiltigförklaras när en produkt uppdateras. Den är dock fortfarande giltig.

<u>Steg som ska återskapas</u>:

1. Utlös följande GraphQL-begäran om du vill få produkter för en viss kategori, som:
   <pre><magento2-server>
    </pre>
1. Spara en av produkterna som hämtats på nytt i Commerce Admin.
1. Utlös begäran igen.

<u>Förväntade resultat</u>:

Rubriken `X-Cache` innehåller `MISS`.

<u>Faktiska resultat</u>:

Rubriken `X-Cache` innehåller `HIT`, vilket innebär att svaret cachelagras.

## Lösning

Inaktivera GraphQL produktcache med den korrigering som finns i den här artikeln.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[MDVA-28559\_EE\_2.3.5-p1\_COMPOSER\_v1.patch](assets/MDVA-28559_EE_2.3.5-p1_v1.composer.patch.zip)

### Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce i molninfrastruktur v2.3.5

Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce i molninfrastruktur v2.4.0
* Adobe Commerce lokalt v2.4.0
* Adobe Commerce om molninfrastruktur v2.3.5-p2
* Adobe Commerce lokalt v2.3.5-p2
* Adobe Commerce i molninfrastruktur v2.3.5-p1
* Adobe Commerce lokal v2.3.5-p1
* Adobe Commerce lokalt v2.3.5
* Adobe Commerce om molninfrastruktur v2.3.4-p2
* Adobe Commerce lokalt v2.3.4-p2
* Adobe Commerce i molninfrastruktur v2.3.4
* Adobe Commerce lokalt v2.3.4
* Adobe Commerce lokalt v2.3.3-p1
* Adobe Commerce lokalt v2.3.3

## Så här sätter du på plåstret

Se [Använda en dispositionsruta från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) för instruktioner om hur du använder en dispositionsruta.

## Bifogade filer
