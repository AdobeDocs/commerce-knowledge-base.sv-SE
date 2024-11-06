---
title: Återställ ett tema till standardvärden
description: Beroende på vilka problem du kan råka ut för när du anpassar dina teman och utvecklar din butik kanske du inte har åtkomst via Commerce Admin. Du kan rensa och återställa till temats standardinställning utan att använda Admin. När du har rensat temat används Luma-standardtemat.
exl-id: 86304dd5-f448-4dcc-ad07-04ecc6c85b6d
feature: Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Återställ ett tema till standardvärden

Beroende på vilka problem du kan råka ut för när du anpassar dina teman och utvecklar din butik kanske du inte har åtkomst via Commerce Admin. Du kan rensa och återställa till temats standardinställning utan att använda Admin. När du har rensat temat används Luma-standardtemat.

Medan du utvecklar Adobe Commerce-komponenter (alla distributioner) och Magento Open Source-komponenter (moduler, teman och språkpaket), kräver den snabbt föränderliga miljön att du regelbundet rensar vissa kataloger och cacheminnen. Annars körs koden med undantag och fungerar inte som den ska. Mer information finns i [Rensa kataloger under utveckling](https://developer.adobe.com/commerce/php/development/components/clear-directories/) i utvecklardokumentationen.

## Miljö och teknik

* Adobe Commerce lokalt
* Adobe Commerce i molninfrastruktur
* Magento Open Source

## Förutsättningar

* Databasverktyg

## Steg

Om du behöver återställa butikstemat men inte kan komma åt administratörspanelen kan du återställa det i databasen genom att göra följande:

1. Använd ett databasverktyg som [phpMyAdmin](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) eller öppna databasen manuellt från kommandoraden för att köra följande SQL-fråga: `UPDATE core_config_data SET value=NULL WHERE path='design/theme/theme_id'`
1. Rensa följande kataloger:
   * `pub/static/frontend`
   * `var/view_preprocessing`
   * `var/cache`
   * `var/page_cache`

På så sätt kommer inget tema att sättas in på visningsnivån för butiken, och när du läser in lagerstartsidorna används Luma-standardtemat.

## Ytterligare information

* [Rensa kataloger under utveckling](https://developer.adobe.com/commerce/php/development/components/clear-directories/) i utvecklardokumentationen
