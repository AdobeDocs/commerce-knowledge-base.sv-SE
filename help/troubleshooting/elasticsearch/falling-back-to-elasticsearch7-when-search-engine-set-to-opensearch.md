---
title: Fallar tillbaka till [!DNL Elasticsearch7] när sökmotorn är inställd på [!DNL Opensearch]
description: Den här artikeln innehåller en lösning på problemet när en *Falling tillbaka till [!DNL Elasticsearch7]* error occurs when the search engine is set to [!DNL OpenSearch] i Adobe Commerce.
feature: Search
role: Developer
exl-id: 965d2929-5cf0-4e0a-9eed-6a656daaa120
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# Fallar tillbaka till [!DNL Elasticsearch7] när sökmotorn är inställd på [!DNL Opensearch]

Den här artikeln innehåller en lösning på problemet när en *Fallar tillbaka till[!DNL Elasticsearch7]* fel inträffar när sökmotorn är inställd på [!DNL OpenSearch] i Adobe Commerce.

## Berörda versioner

Adobe Commerce om molninfrastruktur 2.4.4 - 2.4.5

>[!NOTE]
>
>[!DNL OpenSearch] finns som sökmotor från Adobe Commerce 2.4.6.

## Problem

Du ställer in dina **sökmotor** till **[!DNL OpenSearch]**, men den här typen av fel visas i `var/log/support_report.log` fil:

```[2024-04-04T00:27:41.212916+00:00] report.ERROR: opensearch search engine doesn't exist. Falling back to elasticsearch7 [] []```

<u>Steg som ska återskapas</u>:

1. Verifiera att [!DNL OpenSearch] installeras genom att köra det här kommandot: `curl 127.0.0.1:9200`<br>
Om det indikerar *1.2.4* sedan [!DNL OpenSearch] är redan installerat.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Kontrollera sökmotorn. Det kommer att visas [!DNL Elasticsearch7].

## Orsak

Även om din version stöder [!DNL OpenSearch], programmet bara känner igen/godkänner [!DNL Elasticsearch7] som sökmotor.

Från och med Adobe Commerce version 2.4.6 uppdaterades programmet så att [!DNL OpenSearch] som ska väljas som sökmotor.
Om du går till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** i en icke-molnbaserad miljö kan du ändra det här alternativet så som visas i **Lösning** nedan.
(Obs! I en molnmiljö kan det här fältet inte ändras eftersom sökmotorn är låst i `app/etc/env.php` fil.)

## Lösning

Uppdatera `SEARCH_CONFIGURATION` i `.magento.env.yaml` och se till att **sökmotor** är inställd på *[!DNL elasticsearch7]*.

## Relaterad läsning

[Konfigurera OpenSearch-tjänsten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) i guiden Commerce om molninfrastruktur.
