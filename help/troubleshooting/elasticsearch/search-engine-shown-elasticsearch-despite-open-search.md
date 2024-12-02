---
title: '[!DNL Elasticsearch] visas som sökmotor trots [!DNL OpenSearch] installation'
description: Den här artikeln innehåller en lösning på problemet där  [!DNL Elasticsearch]  fortfarande visas som sökmotor för Adobe Commerce i molnet, även efter installation eller uppgradering till  [!DNL OpenSearch].
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: 1f053f76ae56edc06bfe82e55210244c8ec4b8eb
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# [!DNL Elasticsearch] visas som sökmotor trots [!DNL OpenSearch]-installation

Den här artikeln innehåller en lösning på problemet där [!DNL Elasticsearch] fortfarande visas som sökmotor för Adobe Commerce i molnet, även efter installation eller uppgradering till [!DNL OpenSearch].

## Berörda versioner

Adobe Commerce i molnet 2.4.3-p2 - 2.4.5-p6

>[!NOTE]
>
>[!DNL OpenSearch] är tillgänglig som sökmotor från och med Adobe Commerce 2.4.6.

## Problem

[!DNL Elasticsearch] visas fortfarande som sökmotor för Adobe Commerce i molnet även efter installation eller uppgradering till [!DNL OpenSearch].

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Kontrollera sökmotorn. Det visas [!DNL Elasticsearch7].

## Orsak

Adobe Commerce är hårdkodat för att ange [!DNL Elasticsearch7] som sökmotor.

Detta ska inte blandas ihop med den installerade versionen av tjänsten. Programmet identifierar bara [!DNL Elasticsearch7] som sökmotor, men inte [!DNL OpenSearch], även om den underliggande [!DNL OpenSearch]-tjänsten används som motor i serverdelen.

## Lösning

Kör följande kommando för att verifiera om [!DNL OpenSearch] har installerats:

**Metod 1**:

* Kör följande kommando på servern: `curl 127.0.0.1:9200`. Den ska returnera [!DNL OpenSearch] med sin version.

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

* Använd följande kommando i CLI för Magento-molnet: `magento-cloud relationships -p <project_id>`. Leta reda på [!DNL OpenSearch] när du har använt kommandot.

## Relaterad läsning

[Konfigurera OpenSearch-tjänsten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) i guiden för Commerce om molninfrastruktur.
