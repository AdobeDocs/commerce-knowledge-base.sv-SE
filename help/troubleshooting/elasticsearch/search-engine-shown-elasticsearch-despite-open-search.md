---
title: '[!DNL Elasticsearch] visas som sökmotor trots [!DNL OpenSearch] installation'
description: Den här artikeln innehåller en lösning på problemet där [!DNL Elasticsearch] visas fortfarande som sökmotor för Adobe Commerce i molnet även efter installation eller uppgradering till [!DNL OpenSearch].
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: 1a36e74807e6d32b0810416b6fb61aeca6f9be94
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# [!DNL Elasticsearch] visas som sökmotor trots [!DNL OpenSearch] installation

Den här artikeln innehåller en lösning på problemet där [!DNL Elasticsearch] visas fortfarande som sökmotor för Adobe Commerce i molnet även efter installation eller uppgradering till [!DNL OpenSearch].

## Berörda versioner

Adobe Commerce i molnet 2.4.3-p2 - 2.4.5-p6

>[!NOTE]
>
>[!DNL OpenSearch] finns som sökmotor från Adobe Commerce 2.4.6.

## Problem

[!DNL Elasticsearch] visas fortfarande som sökmotor för Adobe Commerce i molnet även efter installation eller uppgradering till [!DNL OpenSearch].

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Kontrollera sökmotorn. Det kommer att visas [!DNL Elasticsearch7].

## Orsak

Adobe Commerce är hårdkodat att ange [!DNL Elasticsearch7] som sökmotor.

## Lösning

Verifiera om [!DNL OpenSearch] har installerats kör du följande kommando:

**Metod 1**:

* Kör följande kommando på servern: `curl 127.0.0.1:9200`. Den borde returnera [!DNL OpenSearch] med versionen.

**Metod 2**:

* Använd följande kommando i CLI för Magento-cloud: `magento-cloud relationships -p <project_id>`. När du har använt kommandot letar du reda på [!DNL OpenSearch].

## Relaterad läsning

[Konfigurera OpenSearch-tjänsten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) i guiden Commerce om molninfrastruktur.
