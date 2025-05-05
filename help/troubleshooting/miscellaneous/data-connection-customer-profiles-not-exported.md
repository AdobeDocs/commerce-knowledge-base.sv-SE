---
title: Kundprofiler visas inte i Experience Platform
description: I den här artikeln finns felsökningssteg om kundprofildata inte visas i Experience Platform när tillägget  [!DNL Data Connection] används.
feature: Personalization, Integration, Configuration
role: Admin, Developer
exl-id: 4f12b032-0bee-47da-927a-8d4c2d8b8276
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# Kundprofiler visas inte i Experience Platform

I den här artikeln beskrivs felsökningssteg om kundprofildata inte visas i Experience Platform när du använder tillägget Dataanslutning.

## Berörda produkter och versioner

* Adobe Commerce 2.4.x med tillägget [!DNL Data Connection] installerat

## Problem

Du har installerat och konfigurerat tillägget [[!DNL Data Connection]](https://experienceleague.adobe.com/sv/docs/commerce-merchant-services/data-connection/overview) och aktiverat att kundprofildata skickas till Experience Platform, men profildata visas inte i Experience Platform.

## Lösning

Om kundprofilsinformationen inte visas i Experience Platform ska du kontrollera följande:

### Bekräfta att den senaste versionen av [!DNL Data Connection] är installerad

Kontrollera att du har installerat den senaste versionen av tillägget `experience-platform-connector`.

Mer information om den senaste versionen finns i [[!DNL Data Connection] versionsinformationen för tillägget](https://experienceleague.adobe.com/sv/docs/commerce-merchant-services/data-connection/release-notes).

>[!NOTE]
>
>Den senaste versionen av tillägget [!DNL Data Connection] innehåller modulen `customers-connector` som ansvarar för att skicka profildata till Experience Platform. Modulen `customers-connector` ska ha version `1.2.0` eller senare.

### Bekräfta att modulen för kundkoppling är konfigurerad

Bekräfta att modulen `customers-connector` har konfigurerats baserat på ditt installationsscenario.

#### Adobe Commerce i molninfrastruktur

1. Aktivera den globala variabeln `ENABLE_EVENTING` i `.magento.env.yaml`. [Läs mer](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global).

   ```bash
       stage:
           global:
               ENABLE_EVENTING: true
   ```

1. Implementera och skicka uppdaterade filer till molnmiljön. När distributionen är klar aktiverar du skicka händelser med följande kommando:

   ```bash
       bin/magento config:set adobe_io_events/eventing/enabled 1
   ```

#### Lokal installation av Adobe Commerce

Kör följande kommandon för att aktivera kodgenerering och Adobe Commerce Events:

```bash
   bin/magento events:generate:module
   bin/magento module:enable Magento_AdobeCommerceEvents
   bin/magento setup:upgrade
   bin/magento setup:di:compile
   bin/magento config:set adobe_io_events/eventing/enabled 1
```

### Bekräfta att du har aktiverat profildata som ska hämtas och skickas till Experience Platform

Kontrollera att följande fält är angivna i Commerce Admin:

* Kontrollera att kryssrutorna [!UICONTROL Back office events] och [!UICONTROL Customer profiles] är aktiverade i **[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Data Connection]**.
* Kontrollera att fältet *[!UICONTROL Profile Dataset ID]* är korrekt och en annan datamängd än den du använder för beteendedata och bakgrundsdata.

### Kontrollera om händelser dirigeras till staging eller produktion

1. Kör följande kommando för att visa den aktuella Adobe Developer-miljön:

   ```bash
   Copy code
   bin/magento config:show
   adobe_io_events/integration/adobe_io_environment
   ```

1. Om miljön är inställd på *[!UICONTROL Stage]* ändrar du den till *[!UICONTROL Production]* med följande kommando:

   ```bash
   Copy code
   bin/magento config:set adobe_io_events/integration/adobe_io_environment
   production
   ```

### Query Event Data SaaS-tabell

Anslut och kör följande [!DNL SQL]-fråga för att verifiera kundprofilsposter som visas i
`event_data_saas` och att det inte finns några fel:

```sql
Copy code
select * from event_data_saas;
```

### Hantera händelsepubliceringsfel

1. Om följande fel inträffar kontrollerar du att SaaS-anslutningsnycklarna för sandlådan och produktionen är korrekta:

   ```css
   Copy code
   2024-06-07 14:37:57 | 2024-06-07 14:38:03 | 1 | 0 | Event publishing
   failed: Error code: 403; reason: Forbidden { "error": { "code":
   "Forbidden", "message": "Client ID is invalid", "details": {
   "error_code": "403003" } } }
   ```

1. Gå till sidan *[!UICONTROL Commerce Services Connector]* i Admin och kontrollera att de angivna [!UICONTROL sandbox/production]-nycklarna är korrekt konfigurerade. Bekräfta även att inställningarna för Commerce-kontot [!UICONTROL sandbox/production] matchar dem som visas i [!UICONTROL Commerce Services Connector]. Läs [mer](https://experienceleague.adobe.com/sv/docs/commerce-merchant-services/user-guides/integration-services/saas#apikey).

### Kontrollera om tjänst-ID:t finns i tillåtelselista och bekräfta med Adobe Commerce support

1. Kontrollera att [!UICONTROL Commerce Services Connector] `serviceId` visas i tillåtelselista i Adobe Commerce.
1. Kontakta [Adobe Commerce support](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) för att bekräfta tillåtelselista status.

## Relaterad läsning

* [[!DNL Data Connection]](https://experienceleague.adobe.com/sv/docs/commerce-merchant-services/data-connection/overview)-tillägget i användarhandboken för Commerce Services
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
