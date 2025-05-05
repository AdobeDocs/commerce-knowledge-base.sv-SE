---
title: '[!DNL Elasticsearch] visas som sökmotor trots [!DNL OpenSearch] installation'
description: Den här artikeln innehåller en lösning på problemet där  [!DNL Elasticsearch]  fortfarande visas som sökmotor för Adobe Commerce i molnet, även efter installation eller uppgradering till  [!DNL OpenSearch].
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: b3f68e43ce3c4fdea001db1d8ba2774900db7dba
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# [!DNL Elasticsearch] visas som sökmotor trots [!DNL OpenSearch]-installation

Den här artikeln innehåller en lösning på problemet där [!DNL Elasticsearch] fortfarande visas som sökmotor för Adobe Commerce i molnet, även efter installation eller uppgradering till [!DNL OpenSearch].

## Berörda versioner

Adobe Commerce i molnet 2.4.4 - 2.4.5-p11

>[!NOTE]
>
>[!DNL OpenSearch] är tillgänglig som sökmotor från och med Adobe Commerce 2.4.6.

## Problem

[!DNL Elasticsearch] visas fortfarande som sökmotor för Adobe Commerce i molnet även efter installation eller uppgradering till [!DNL OpenSearch].

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Kontrollera sökmotorn. Det visas [!DNL Elasticsearch7].

## Orsak

[!DNL Elasticsearch7] är hårdkodad i Adobe Commerce för att vara sökmotorn som används i dessa versioner.

Detta ska inte blandas ihop med den installerade versionen av tjänsten. Även om det inte finns någon [!DNL Opensearch]-modul i koden kan Adobe Commerce använda den underliggande [!DNL Opensearch]-tjänsten.

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

* Använd följande kommando i Magento-cloud CLI: `magento-cloud relationships -p <project_id>`. Leta reda på [!DNL OpenSearch] när du har använt kommandot.

## Relaterad läsning

[Konfigurera OpenSearch-tjänsten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html?lang=sv-SE) i guiden för Commerce om molninfrastruktur.
