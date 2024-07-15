---
title: Fel [!DNL opensearch] sökmotorn finns inte. Återgår till  [!DNL livesearch].
description: Den här artikeln innehåller en lösning på problemet där felet "Fel- [!DNL opensearch] sökmotorn finns inte. Fallar tillbaka till  [!DNL livesearch].", i Adobe Commerce om molninfrastruktur.
feature: Deploy, Search
role: Developer
exl-id: a6cc981d-b8f0-402d-8771-60d2f21f09f8
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# Sökmotorn för felet [!DNL opensearch] finns inte. Återgår till [!DNL livesearch].

Den här artikeln innehåller en lösning på problemet där felet visas: *Fel: [!DNL opensearch] sökmotorn finns inte. Återgår till [!DNL livesearch].* i Adobe Commerce i molninfrastruktur där [!DNL Live Search] används.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur, alla versioner
* [!DNL Live Search] är installerat och används

## Problem

Följande meddelande visas i loggarna (och kan observeras i [!DNL New Relic]):
*Fel: [!DNL opensearch] Sökmotorn finns inte. Återgår till [!DNL livesearch].*

## Lösning

1. Ändra filen `.magento.env.yaml`.
1. Leta reda på följande rader:

   ```yaml
     deploy:
   ...
       SEARCH_CONFIGURATION:
         engine: opensearch
   ```

1. Om du inte har dessa rader lägger du till dem i filen `.magento.env.yaml`.
1. Om de här raderna finns ändrar **motorn** från *[!DNL opensearch]* till *[!DNL livesearch]*.
1. Genomför ändringen och distribuera sedan på nytt.

## Relaterad läsning

* [Installera [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) i vår Live Search-guide
