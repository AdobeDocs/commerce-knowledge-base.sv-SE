---
title: Återgår till  [!DNL Elasticsearch7] när sökmotorn är inställd på  [!DNL Opensearch]
description: Den här artikeln innehåller en lösning på problemet när en *Falling back to [!DNL Elasticsearch7]* error occurs when the search engine is set to [!DNL OpenSearch] in Adobe Commerce.
feature: Search
role: Developer
exl-id: 965d2929-5cf0-4e0a-9eed-6a656daaa120
source-git-commit: d17af0f8f92726aa5a6914fc9e1ff13268256d04
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Återgår till [!DNL Elasticsearch7] när sökmotorn är inställd på [!DNL Opensearch]

Den här artikeln innehåller en lösning på problemet när ett *fel som returneras till[!DNL Elasticsearch7]* inträffar när sökmotorn är inställd på [!DNL OpenSearch] i Adobe Commerce.

## Berörda versioner

Adobe Commerce i molninfrastruktur
2.4.4 - 2.4.4-p12
2.4.5 - 2.4.5-p11

>[!NOTE]
>
>[!DNL OpenSearch] är tillgängligt som sökmotor från Adobe Commerce 2.4.6, 2.4.5-p12, 2.4.4-p13.

## Problem

Du har angett **sökmotorn** till **[!DNL OpenSearch]**, men du kan se den här typen av fel i filen `var/log/support_report.log`:

```[2024-04-04T00:27:41.212916+00:00] report.ERROR: opensearch search engine doesn't exist. Falling back to elasticsearch7 [] []```

<u>Steg som ska återskapas</u>:

1. Kontrollera att [!DNL OpenSearch] är installerat genom att köra det här kommandot: `curl 127.0.0.1:9200`<br>
Om det anger *1.2.4* är [!DNL OpenSearch] redan installerat.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Kontrollera sökmotorn. Det visas [!DNL Elasticsearch7].

## Orsak

Även om din version har stöd för [!DNL OpenSearch], kommer programmet endast att identifiera/acceptera [!DNL Elasticsearch7] som sökmotor.

Från och med Adobe Commerce version 2.4.6 uppdaterades programmet så att [!DNL OpenSearch] kan väljas som sökmotor.
Om du går till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** i en icke-molnmiljö, kan du ändra det här alternativet enligt **Lösning** nedan.
(Obs! I en molnmiljö går det inte att ändra det här fältet eftersom sökmotorn är låst i filen `app/etc/env.php`.)

## Lösning

Uppdatera variabeln `SEARCH_CONFIGURATION` i filen `.magento.env.yaml` och se till att **sökmotorn** är inställd på *[!DNL elasticsearch7]*.

## Relaterad läsning

[Konfigurera OpenSearch-tjänsten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) i guiden för Commerce om molninfrastruktur.
