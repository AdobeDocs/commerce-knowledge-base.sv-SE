---
title: Distributionsfel där korrigeringar inte hittas
description: "Den här artikeln innehåller en lösning på problemet där du ser ett fel *Nästa korrigeringsfiler hittades inte: MDVA-XXXXX, ACSD-XXXXX. Kontrollera med kommandot 'status' att dessa korrigeringsfiler för den aktuella Magento-versionen* är tillgängliga."
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Distributionsfel där korrigeringar inte hittas

I den här artikeln finns en lösning på problemet när du uppgraderar din instans. Distributionen misslyckas och du ser ett fel i distributionsloggarna: *Det gick inte att hitta nästa patchar: MDVA-XXXXX, ACSD-XXXXX. Kontrollera med&quot;status&quot;-kommandot att dessa patchar för den aktuella Magento-versionen är tillgängliga*.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur, [alla versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).


## Problem

Du får ett fel när du uppgraderar Adobe Commerce: *Det gick inte att hitta nästa korrigering*.

## Orsak

Patchar som tidigare har tillämpats för äldre versioner är inte tillämpliga eller inte längre tillgängliga för den nya versionen.

## Lösning

1. Kontrollera `.magento.env.yaml` under avsnittet QUALITY_PATCH, t.ex.

   ```yaml
   QUALITY_PATCHES:
    - MDVA-XXXXX
    - ACSD-XXXXX
   ```

1. Söka efter korrigerings-ID:n i [Versionsinformation om kvalitetsuppdateringar](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) för att kontrollera om var och en kan användas i den nya versionen av Adobe Commerce som du uppgraderar till.
1. Om korrigeringen inte gäller för den nya versionen av Adobe Commerce som du vill uppgradera till tar du bort patch-ID:t från `.magento.env.yaml` -fil.
1. När du har granskat alla korrigerings-ID:n som anges av felet skickar du ändringarna och distribuerar om.

## Relaterad läsning

* [Tillämpa patchar](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=en#apply-a-patch-in-a-local-environment) i Commerce om Cloud Infrastructure Guide.
