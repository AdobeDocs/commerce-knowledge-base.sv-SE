---
title: Cacheuppvärmning och webbplatsen är inte tillgänglig i Adobe Commerce
description: Den här artikeln innehåller en lösning för när sidcachen värms upp och det finns en fast distribution eller en webbplats som inte fungerar.
exl-id: c91d5c1f-95e6-4240-be98-2acea49ae728
feature: Cache, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Cacheuppvärmning och webbplatsen är inte tillgänglig i Adobe Commerce

Den här artikeln innehåller en lösning för när sidcachen värms upp och det finns en fast distribution eller en webbplats som inte fungerar.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen, alla [versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problem

Skriptet för cachelagring, i slutet av efterdistribueringsfasen, skickar begäranden i en så hög hastighet att vissa instanser, som 4-cpu-instanser, inte kan hantera. Deras nginx gör att antalet arbetstagare blir otillräckligt.

<u>Steg som ska återskapas</u>:

Starta cacheuppvärmningsåtgärder.

<u>Förväntat resultat</u>:

Sidor eller hela platsen läses in.

<u>Faktiskt resultat</u>:

Webbplatsen är inte tillgänglig eller så är svarstiden för hög.

## Lösning

Begränsa antalet samtidiga anslutningar under cacheuppvarningen. Detta kräver att variabeln `WARM_UP_CONCURRENCY` post-deploy läggs till för att ange antalet uppvärmningsbegäranden som cacheuppvärmarskriptet kan skicka samtidigt. Om du anger det här alternativet kan belastningen på Adobe Commerce molninfrastruktur hanteras. Anvisningar finns i [Efterdistribuera variabler > WARM\_UP\_CONCURRENCY](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-post-deploy#warm_up_concurrency) i vår utvecklardokumentation.

## Relaterad läsning

[Helsidescache](https://experienceleague.adobe.com/sv/docs/commerce-admin/systems/tools/cache-management#full-page-caching) i användarhandboken
