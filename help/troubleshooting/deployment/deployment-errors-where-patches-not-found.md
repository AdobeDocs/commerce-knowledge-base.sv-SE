---
title: Distributionsfel där korrigeringar inte hittas
description: 'Den här artikeln innehåller en lösning på problemet där ett fel uppstod *Nästa korrigeringsfiler inte hittades: MDVA-XXXXX, ACSD-XXXXX. Kontrollera med kommandot ''status'' att dessa korrigeringsfiler för den aktuella Magento-versionen* är tillgängliga.'
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Distributionsfel där korrigeringar inte hittas

Den här artikeln innehåller en lösning på problemet när du uppgraderar din instans. Distributionen misslyckas och du ser ett fel i distributionsloggarna: *Det gick inte att hitta nästa korrigeringsfil: MDVA-XXXXX, ACSD-XXXXX. Kontrollera med&quot;status&quot;-kommando att dessa korrigeringar är tillgängliga för den aktuella Magento-versionen*.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen, [alla versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).


## Problem

Ett fel uppstod när du uppgraderade Adobe Commerce: *Det gick inte att hitta nästa korrigeringsfil*.

## Orsak

Patchar som tidigare har tillämpats för äldre versioner är inte tillämpliga eller inte längre tillgängliga för den nya versionen.

## Lösning

1. Kontrollera filen `.magento.env.yaml` under avsnittet QUALITY_PATCH, t.ex.,

   ```yaml
   QUALITY_PATCHES:
    - MDVA-XXXXX
    - ACSD-XXXXX
   ```

1. Leta reda på korrigerings-ID:n i [Versionsinformation för kvalitetsuppdateringar](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) för att kontrollera om var och en kan användas för den nya versionen av Adobe Commerce som du uppgraderar till.
1. Om korrigeringen inte gäller för den nya versionen av Adobe Commerce som du vill uppgradera till tar du bort korrigerings-ID:t från filen `.magento.env.yaml`.
1. När du har granskat alla korrigerings-ID:n som anges av felet skickar du ändringarna och distribuerar om.

## Relaterad läsning

* [Använd korrigeringsfiler](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=en#apply-a-patch-in-a-local-environment) i Commerce i molninfrastrukturguiden.
