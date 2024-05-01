---
title: Cacheuppvärmning och webbplatsen är inte tillgänglig i Adobe Commerce
description: Den här artikeln innehåller en lösning för när sidcachen värms upp och det finns en fast distribution eller en webbplats som inte fungerar.
exl-id: c91d5c1f-95e6-4240-be98-2acea49ae728
feature: Cache, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Cacheuppvärmning och webbplatsen är inte tillgänglig i Adobe Commerce

Den här artikeln innehåller en lösning för när sidcachen värms upp och det finns en fast distribution eller en webbplats som inte fungerar.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen, alla [versionerna](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problem

Skriptet för cachelagring, i slutet av efterdistribueringsfasen, skickar begäranden i en så hög hastighet att vissa instanser, som 4-cpu-instanser, inte kan hantera. Deras nginx gör att antalet arbetstagare blir otillräckligt.

<u>Steg som ska återskapas</u>:

Starta cacheuppvärmningsåtgärder.

<u>Förväntat resultat</u>:

Sidor eller hela platsen läses in.

<u>Faktiskt resultat</u>:

Webbplatsen är inte tillgänglig eller så är svarstiden för hög.

## Lösning

Begränsa antalet samtidiga anslutningar under cacheuppvarningen. Detta kräver att du lägger till `WARM_UP_CONCURRENCY` variabel efter distribution för att ange antalet uppvärmningsbegäranden som cacheuppvärmarskriptet kan skicka samtidigt. Om du anger det här alternativet kan belastningen på Adobe Commerce molninfrastruktur hanteras. Om du vill se steg går du till [Variabler efter distribution > WARM\_UP\_CONCURRENCY](https://devdocs.magento.com/cloud/env/variables-post-deploy.html#warm_up_concurrency) i vår dokumentation för utvecklare.

## Relaterad läsning

[Helsidescache](https://docs.magento.com/user-guide/system/cache-full-page.html) i vår användarhandbok
