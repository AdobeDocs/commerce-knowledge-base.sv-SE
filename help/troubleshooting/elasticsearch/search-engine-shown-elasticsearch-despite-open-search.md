---
title: '[!DNL Elasticsearch] visas som sökmotor trots [!DNL OpenSearch] installation'
description: Den här artikeln innehåller en lösning på problemet där [!DNL Elasticsearch] visas fortfarande som sökmotor för Adobe Commerce i molnet även efter installation eller uppgradering till [!DNL OpenSearch].
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: 1f053f76ae56edc06bfe82e55210244c8ec4b8eb
workflow-type: tm+mt
source-wordcount: '223'
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

Detta ska inte blandas ihop med den installerade versionen av tjänsten. Programmet känner bara igen [!DNL Elasticsearch7] som sökmotor, men inte [!DNL OpenSearch]även om den använder det underliggande [!DNL OpenSearch] som motor i serverdelen.

## Lösning

Verifiera om [!DNL OpenSearch] har installerats kör du följande kommando:

**Metod 1**:

* Kör följande kommando på servern: `curl 127.0.0.1:9200`. Den borde returnera [!DNL OpenSearch] med versionen.

Exempel:

```
$ curl 127.0.0.1:9200
{
  "name" : $clusterName,
  "cluster_name" : "opensearch_stg",
  "cluster_uuid" : $clusterUuid,
  "version" : {
    "distribution" : "opensearch",
    "number" : "1.2.4",
    "build_type" : "deb",
    "build_hash" : "44ccdbaed5fe5a8b02d99a611857a671b6dd909d",
    "build_date" : "2022-11-08T09:23:45.993372Z",
    "build_snapshot" : false,
    "lucene_version" : "8.10.1",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "The OpenSearch Project: https://opensearch.org/"
}
```

**Metod 2**:

* Använd följande kommando i CLI för Magento-cloud: `magento-cloud relationships -p <project_id>`. När du har använt kommandot letar du reda på [!DNL OpenSearch].

## Relaterad läsning

[Konfigurera OpenSearch-tjänsten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) i guiden Commerce om molninfrastruktur.
