---
title: Utelämna fördröjning vid problem med inloggning eller utcheckning av Commerce Admin
description: Den här artikeln innehåller en korrigering av problemet när du loggar in på Commerce Admin eller öppnar utcheckningssidan som orsakar fördröjning eller timeout (mer än 30 sekunder). Problemet inträffar när Redis används för sessionslagring.
exl-id: a91a7a51-7cc4-4910-a9de-3a212788663f
feature: Admin Workspace, Checkout, Orders, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Utelämna fördröjning vid problem med inloggning eller utcheckning av Commerce Admin

Den här artikeln innehåller en korrigering av problemet när du loggar in på Commerce Admin eller öppnar utcheckningssidan som orsakar fördröjning eller timeout (mer än 30 sekunder). Problemet inträffar när Redis används för sessionslagring.

**Orsak:**   [Github-utgåva \#12385](https://github.com/magento/magento2/issues/12385) .

**Lösning:** Uppdatera till den senaste Adobe Commerce-korrigeringen för att åtgärda problemen för alla versioner av Redis och särskilda versioner av Adobe Commerce.

## Berörda versioner och tekniker

* Adobe Commerce on cloud infrastructure versions 2.1.11 - 2.1.13 and 2.2.1
* Adobe Commerce lokala versioner 2.1.11 - 2.1.13 och 2.2.1
* Redis, alla versioner

Om du använder Adobe Commerce i molninfrastrukturversionen [2.2.0](#h_64593789291526919876198) finns det en lösning.

## Problem

Det tar över 30 sekunder att logga in på Commerce Admin eller gå vidare till utcheckningssidan.

Detta inträffar endast när användarsessioner lagras i Redis.

## Orsak

Adobe Commerce hade problem med sessionslåsmekanismen som lade till en 30-sekunders timeout till vissa åtgärder när Redis användes för sessionslagring. Mer information finns i [Github-utgåvan \#12385](https://github.com/magento/magento2/issues/12385).

Problemet har åtgärdats i Adobe Commerce 2.1.14 och 2.2.2.

## Lösningar: korrigering eller uppgradering

### Lösning 1: Lägg på patchen med en fix

[Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) och begär korrigeringen för att få en korrigering. Ange din Adobe Commerce-version och motsvarande referensnummer för korrigeringen i din biljett:

* **2.1.11 och senare:** MDVA-7835
* **2.2.1:** MDVA-8128

Det allmänna referensnumret (versionsanpassat) är MAGETWO-84289.

### Lösning 2: Uppgradera till 2.1.14/2.2.2 eller senare

Om du tidigare har övervägt att uppgradera till Adobe Commerce 2.2.2 eller senare kan du använda den här uppdateringsmöjligheten för att åtgärda problemet.

## Tillfällig lösning: inaktivera sessionslås

Om du vill inaktivera sessionslås anger du `disable_locking` till `1` i Redis-konfigurationsavsnittet i filen `env.php`:

```php
'session' =>
  array (
    'save' => 'redis',
    'redis' =>
    array (
      'host' => 'redis.internal',
      'port' => 6379,
      'database' => '0',
      'disable_locking' => '1'
    ),
  ),
```

Den här lösningen påverkar inte några andra Adobe Commerce-funktioner.

### Återgå till tillfällig lösning när du har använt korrigeringen

När du har tillämpat korrigeringen med korrigeringen behövs inte lösningen längre, så du kan återställa den (ange `disable_locking` till `0`).

## Adobe Commerce om molninfrastruktur 2.2.0: använd ECE-Tools v2002.0.8 eller senare {#h_64593789291526919876198}

Distributionsskriptpaketet [ECE-Tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package) med version 2002.0.3 - 2002.0.7 [tillämpar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) lösningen automatiskt med inställningen `disable_locking` till `1`. Detta inaktiverar sessionslåsmekanismen för Adobe Commerce 2.2.0, där det ursprungliga problemet inte uppstår.

Om du kör Adobe Commerce i molninfrastruktur 2.2.0 ska du uppgradera ECE-Tools till v2002.0.8 eller senare. Du kan också överväga att uppgradera din Adobe Commerce i molninfrastruktur till 2.2.2 eller senare.
