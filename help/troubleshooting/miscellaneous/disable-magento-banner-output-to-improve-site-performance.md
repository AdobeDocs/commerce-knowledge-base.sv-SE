---
title: Inaktivera utdata från Adobe Commerce Banner för att förbättra webbplatsens prestanda
description: Den här artikeln innehåller en korrigering för låg webbplatsprestanda. Låga prestanda kan orsakas av att modulen "Magento_Banner" är aktiverad men inte används. Om du inaktiverar modulutdata kan platsens prestanda förbättras. Läs artikeln för att se hur lösningen fungerar.
exl-id: 90a8bd21-1f2c-4cfe-8213-17f877e20de8
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Inaktivera utdata från Adobe Commerce Banner för att förbättra webbplatsens prestanda

Den här artikeln innehåller en korrigering för låg webbplatsprestanda. Låga prestanda kan orsakas av `Magento_Banner` modulen aktiveras men används inte. Om du inaktiverar modulutdata kan platsens prestanda förbättras. Läs artikeln för att se hur lösningen fungerar.

>[!NOTE]
>
>Om du använder funktionen Adobe Commerce Banner kan du läsa [Hög genomströmning AJAX begäranden orsakar dålig prestanda](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) artikel i vår kunskapsbas för support med rekommendationer om hur du undviker prestandaproblem som orsakas av för många Ajax-förfrågningar.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur v.2.x.x
* Adobe Commerce lokal v.2.2.x och 2.3.x

## Problem

The `Magento_Banner` modulen är aktiverad, men används inte.

Så här kontrollerar du om så är fallet:

För Adobe Commerce om molninfrastruktur 2.2.x:

1. Logga in på Commerce Admin.
1. Navigera till **Innehåll** > *Element* > **Banderoller**.
1. Om rutnätet som visas på den här sidan är tomt har du inga banners.

Om du inte ser **Banderoller** option under **Innehåll** > *Element* så är detta inte fallet och rekommendationerna från den här artikeln kan inte tillämpas.

För Adobe Commerce i molninfrastruktur 2.3.x (funktionen var [bytt namn i v 2.3.x](https://devdocs.magento.com/guides/v2.3/release-notes/ReleaseNotes2.3.0Commerce.html#banner-now-dynamic-block)):

1. Logga in på Commerce Admin.
1. Navigera till **Innehåll** > *Elements >*  **Dynamiska block**.
1. Om rutnätet som visas på den här sidan är tomt har du inga dynamiska block (banners).

Om du inte ser **Dynamiska block** option under **Innehåll** > *Element* så är detta inte fallet och rekommendationerna från den här artikeln kan inte tillämpas.

## Orsak

När `Magento_Banner` När modulen är aktiverad skickar Adobe Commerce Ajax-begäranden från butiken till servern för att få information om banderollen. Dessa Ajax-förfrågningar har en inverkan på prestandan, särskilt vid stora volymer och hög trafik. Om funktionen inte används bör du inaktivera modulutdata. Du bör inte inaktivera modulen på grund av beroendeproblem.

## Lösning

>[!WARNING]
>
>Vi rekommenderar att du testar ändringar på [Mellanlagrings-/integreringsmiljö](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) först, innan du använder det i Produktion. Vi rekommenderar även att du har en säkerhetskopia nyligen före eventuella ändringar.

1. Inaktivera `Magento_Banner` modulutdata enligt beskrivningen i [Inaktivera modulutdata](https://devdocs.magento.com/guides/v2.3/config-guide/config/disable-module-output.html) i vår dokumentation för utvecklare. Modulnamnet som du behöver använda är `Magento_Banner`.
1. Distribuera koden. För Adobe Commerce i molninfrastruktur ska du driftsätta enligt anvisningarna i [Distribuera din butik](https://devdocs.magento.com/guides/v2.3/cloud/live/stage-prod-live.html) artikel i vår dokumentation för utvecklare.
