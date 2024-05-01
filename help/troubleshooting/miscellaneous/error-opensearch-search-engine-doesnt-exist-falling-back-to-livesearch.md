---
title: Fel [!DNL opensearch] sökmotorn finns inte. Fallar tillbaka till [!DNL livesearch].
description: I den här artikeln finns en lösning på problemet där felet uppstod, "Error- [!DNL opensearch] sökmotorn finns inte. Fallar tillbaka till [!DNL livesearch].", i Adobe Commerce om molninfrastruktur.
feature: Deploy, Search
role: Developer
exl-id: a6cc981d-b8f0-402d-8771-60d2f21f09f8
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# Fel [!DNL opensearch] sökmotorn finns inte. Fallar tillbaka till [!DNL livesearch].

I den här artikeln finns en lösning på problemet där du ser felet: *Fel: [!DNL opensearch] sökmotorn finns inte. Fallar tillbaka till [!DNL livesearch].* i Adobe Commerce om molninfrastruktur där [!DNL Live Search] används.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur, alla versioner
* [!DNL Live Search] är installerat och används

## Problem

Följande meddelande visas i loggarna (och kan ses i [!DNL New Relic]):
*Fel: [!DNL opensearch] sökmotorn finns inte. Fallar tillbaka till [!DNL livesearch].*

## Lösning

1. Ändra `.magento.env.yaml` -fil.
1. Leta reda på följande rader:

   ```yaml
     deploy:
   ...
       SEARCH_CONFIGURATION:
         engine: opensearch
   ```

1. Om du inte har dessa rader lägger du till dem i `.magento.env.yaml` -fil.
1. Om dessa rader finns, **ändra motorn** från *[!DNL opensearch]* till *[!DNL livesearch]*.
1. Genomför ändringen och distribuera sedan på nytt.

## Relaterad läsning

* [Installera [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) i vår Live Search-guide
