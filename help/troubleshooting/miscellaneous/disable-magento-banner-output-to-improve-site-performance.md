---
title: Inaktivera utdata från Adobe Commerce Banner för att förbättra webbplatsens prestanda
description: Den här artikeln innehåller en korrigering för låg webbplatsprestanda. Låga prestanda kan bero på att modulen "Magento_Banner" är aktiverad men inte används. Om du inaktiverar modulutdata kan platsens prestanda förbättras. Läs artikeln för att se hur lösningen fungerar.
exl-id: 90a8bd21-1f2c-4cfe-8213-17f877e20de8
feature: Configuration
role: Developer
source-git-commit: 76ef59dc37504f50d55734a90c9ce5b30bb83175
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Inaktivera utdata från Adobe Commerce Banner för att förbättra webbplatsens prestanda

Den här artikeln innehåller en korrigering för låg webbplatsprestanda. Låga platsprestanda kan orsakas av att modulen `Magento_Banner` aktiveras men inte används. Om du inaktiverar modulutdata kan platsens prestanda förbättras. Läs artikeln för att se hur lösningen fungerar.

>[!NOTE]
>
>Om du använder Adobe Commerce Banner-funktionen läser du artikeln [Hög genomströmning för AJAX orsakar dålig prestanda](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) i vår kunskapsbas för support där du hittar rekommendationer om hur du undviker prestandaproblem som orsakas av för många Ajax-begäranden.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur v.2.x.x
* Adobe Commerce lokal v.2.2.x och 2.3.x

## Problem

Modulen `Magento_Banner` är aktiverad, men används inte.

Så här kontrollerar du om så är fallet:

För Adobe Commerce om molninfrastruktur 2.2.x:

1. Logga in på Commerce Admin.
1. Navigera till **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Banners]**.
1. Om rutnätet som visas på den här sidan är tomt har du inga banners.

Om du inte ser alternativet **[!UICONTROL Banners]** under **[!UICONTROL Content]** > **[!UICONTROL Elements]** betyder det att du redan har tillämpat rekommendationerna från den här artikeln.

För Adobe Commerce i molninfrastruktur 2.3.x och senare (funktionen [döptes om i v 2.3.x](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/ReleaseNotes2.3.0Commerce.html#banner-now-dynamic-block)):

1. Logga in på Commerce Admin.
1. Navigera till **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Dynamic Blocks]**.
1. Om rutnätet som visas på den här sidan är tomt har du inga dynamiska block (banners).

Om du inte ser alternativet **[!UICONTROL Dynamic Blocks]** under **[!UICONTROL Content]** > **[!UICONTROL Elements]** betyder det att du redan har tillämpat rekommendationen från den här artikeln. Om du vill visa banneralternativet igen ångrar du processen.

## Orsak

När modulen `Magento_Banner` är aktiverad skickar Adobe Commerce Ajax-förfrågningar från butiken till servern för att hämta banderollinformationen. Dessa Ajax-förfrågningar har en inverkan på prestandan, särskilt vid stora volymer och hög trafik. Om funktionen inte används bör du inaktivera modulutdata. Du bör inte inaktivera modulen på grund av beroendeproblem.

## Lösning

>[!WARNING]
>
>Vi rekommenderar att du först testar ändringar i [mellanlagrings-/integreringsmiljön](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) innan du använder dem i produktionen. Vi rekommenderar även att du har en säkerhetskopia nyligen före eventuella ändringar.

1. Inaktivera `Magento_Banner`-modulens utdata enligt beskrivningen i [Inaktivera modulutdata](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/files/disable-module-output) i utvecklardokumentationen. Modulnamnet som du måste använda är `Magento_Banner`.
1. Distribuera koden. För Adobe Commerce i molninfrastruktur distribuerar du enligt beskrivningen i artikeln [Distribuera din butik](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production) i vår utvecklardokumentation.
1. När modulutdata har inaktiverats visas inte längre menyn i administratören.
1. Du kommer inte längre att se alternativet Banner eller Dynamisk under **[!UICONTROL Content]** > **[!UICONTROL Elements]**. [aktivera modulutdata](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/files/disable-module-output?lang=en#disable-module-output-in-a-simple-deployment) om du vill visa alternativen igen.

