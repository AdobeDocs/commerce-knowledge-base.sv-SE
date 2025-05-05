---
title: MySQL och Elasticsearch visar olika resultat
description: I den här artikeln finns en patch för det kända problemet med Adobe Commerce i molninfrastruktur 2.2.3 som rör hämtning av olika sökresultat för samma sökfråga med MySQL och Elasticsearch.
exl-id: 37a0164a-0237-4200-ab9c-e0dbad7e2062
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MySQL och Elasticsearch visar olika resultat

>[!WARNING]
>
> [MySQL-katalogsökmotorn tas bort i Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Elasticsearch-värden måste vara konfigurerad och konfigurerad innan du kan installera version 2.4.0. Mer information finns i [Installera och konfigurera Elasticsearch](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/search/overview-search) i utvecklardokumentationen.

I den här artikeln finns en patch för det kända problemet med Adobe Commerce i molninfrastruktur 2.2.3 som rör hämtning av olika sökresultat för samma sökfråga med MySQL och Elasticsearch.

## Problem:

Vilka katalogsökresultat som har samma filteruppsättning skiljer sig åt beroende på vilken sökmotor som används, MySQL eller Elasticsearch.

<u>Steg som ska återskapas</u> :

1. Installera och konfigurera Elasticsearch.
1. Välj ett av filtren i butiken.
1. Notera antalet matchande produkter.
1. Konfigurera [MySQL-standardsökningen](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md).
1. Välj ett av filtren i butiken.
1. Notera antalet matchande produkter.

<u>Förväntat resultat</u>:
Antalet matchande produkter är detsamma.

<u>Faktiskt resultat</u>:
Antalet matchande produkter är annorlunda.

## Lappa

Patcherna är kopplade till den här artikeln. Om du vill hämta en patch rullar du nedåt till slutet av artikeln och klickar på önskat filnamn, eller klickar på följande länkar:

[Hämta MDVA-12312\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-12312_EE_2.2.3_COMPOSER_v1.patch.zip)

[Hämta MDVA-14172\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-14172_EE_2.2.6_COMPOSER_v1.patch.zip)

### Kompatibla Adobe Commerce-versioner:

Patcharna skapades för:

* Adobe Commerce om molninfrastruktur 2.2.3 (filen `MDVA-12312_EE_2.2.3_COMPOSER_v1.patch`)
* Adobe Commerce om molninfrastruktur 2.2.6 (filen `MDVA-14172_EE_2.2.6_COMPOSER_v1.patch`)

Korrigeringen `MDVA-12312_EE_2.2.3_COMPOSER_v1.patch` är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce i molninfrastruktur 2.2.4
* Adobe Commerce om molninfrastruktur 2.2.5
* Adobe Commerce lokal 2.2.3
* Adobe Commerce lokal 2.2.4
* Adobe Commerce lokal 2.2.5

Korrigeringen `MDVA-14172_EE_2.2.6_COMPOSER_v1.patch` är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce lokal 2.2.6

## Så här sätter du på plåstret

Mer information finns i [Använda en dispositionsruta från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.

## Bifogade filer
