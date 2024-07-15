---
title: Distributionen fastnade med felet"Det gick inte att överföra programmet till fjärrklustret"
description: '"Den här artikeln innehåller en lösning på Adobe Commerce-problemet, där distributionen fastnar och följande felmeddelande finns i distributionsloggen: *"Fel: Det går inte att överföra programmet till fjärrklustret"*."'
exl-id: 30f0ec31-db27-429c-b065-cf7770a72194
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Distributionen fastnade med felet&quot;Det gick inte att överföra programmet till fjärrklustret&quot;

Den här artikeln innehåller en lösning på Adobe Commerce-problemet, där distributionen fastnar och följande felmeddelande finns i distributionsloggen: *&quot;Fel: Det går inte att överföra programmet till fjärrklustret&quot;*.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur, alla versioner

## Problem

<u>Steg som ska återskapas</u>:

Utlös distributionen manuellt eller genom att utföra en sammanslagning, push eller synkronisering av din miljö.

<u>Förväntat resultat</u>:

Distributionen har slutförts.

<u>Faktiskt resultat</u>:

Distributionen fastnar och i distributionsfelloggen i molngränssnittet visas följande felmeddelande: *&quot;Fel: Det går inte att överföra programmet till fjärrklustret&quot; som hittades i distributionsloggen efter misslyckad distribution. Platsen kan visa felet 503 timeout för första byte*.

## Orsak

Problemet beror på brist på tillgängligt lagringsutrymme.

## Lösning

Du kan överväga att rensa loggkatalogerna och/eller öka diskutrymmet.

Kataloger som ska rensas:

* `var/log`
* `var/report`
* `var/debug/`
* `var`

Mer information om hur du kan öka diskutrymmet om du använder Adobe Commerce i arkitekturen för startplaner för molninfrastruktur finns i [Öka diskutrymmet för integreringsmiljön i molnet](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md) i vår supportdatabas. Samma instruktioner kan användas för att öka utrymmet för Adobe Commerce i molninfrastrukturen Pro-planarkitekturintegreringsmiljön. För Pro Production/Staging måste du [registrera en biljett till Adobe Commerce Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket-Submit-a-support-ticket) och begära utökat diskutrymme. I vanliga fall behöver du inte hantera detta när Pro-planen mellanlagras/produceras eftersom Adobe Commerce övervakar parametrarna åt dig och varnar och/eller vidtar åtgärder enligt avtalet.
