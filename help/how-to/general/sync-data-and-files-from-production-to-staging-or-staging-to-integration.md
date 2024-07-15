---
title: Synkronisera data och filer Produktion till Förproduktion eller Förproduktion till integrering
description: I den här artikeln beskrivs hur du synkroniserar din produktionsmiljö ända till Staging på Adobe Commerce i molninfrastrukturen. Detta är inte möjligt.
exl-id: e3d001d1-1b2a-41b5-9b4a-00e53dc9d001
feature: Integration, Build
source-git-commit: ef294ddc9c4a12b06ce7738cb4702253dd892f3b
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Synkronisera data och filer Produktion till Förproduktion eller Förproduktion till integrering

I den här artikeln beskrivs hur du synkroniserar din produktionsmiljö ända till Staging på Adobe Commerce i molninfrastrukturen. Detta är inte möjligt via användargränssnittet eller Magento-cloud CLI.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.3.x, 2.4.x

## Synkronisera data från en miljö till en annan

Om du vill synkronisera data måste du manuellt dumpa databasen från källmiljön. Om du vill överföra data till en annan miljö måste du sedan överföra källdumpen till målmiljön och importera den. Mer information finns i [Importera Adobe Commerce-kod till ett molnprojekt > Importera Adobe Commerce-databas](https://devdocs.magento.com/cloud/setup/first-time-setup-import-import.html) i utvecklardokumentationen.

För Adobe Commerce på Cloud Infrastructure Pro-planarkitekturen kan du även synkronisera från Förproduktion och Produktion till din Integration Master-gren. Synkroniseringen hämtar och push-tar bara fram kod, inte data. Om du vill synkronisera data måste du dumpa databasdata och överföra dem till en annan miljös databas.

>[!WARNING]
>
>Det går inte att synkronisera databasen i Pro Staging- och Production-klustren.

## Synkronisera filer från en miljö till en annan

Om du vill synkronisera filer från en miljö till en annan använder du kommandot `rsync`. Mer information finns i [Distribuera kod och migrera statiska filer och data > Migrera filer med hjälp av synkronisering](https://devdocs.magento.com/cloud/live/stage-prod-migrate.html#migrate-files-using-rsync) i utvecklardokumentationen.

>[!NOTE]
>
>Om du vill synkronisera koden från Integrering till Förproduktion måste du göra det från grenen Integrering. Anvisningar finns i [Synkronisera från miljöns överordnade](/docs/commerce-cloud-service/user-guide/project/console-branches.html#sync-an-environment) i utvecklardokumentationen.
