---
title: Katalogsidindelning fungerar inte med Elasticsearch 6.x
description: I den här artikeln finns en patch för Adobe Commerce-problemet där katalogsidnumrering inte fungerar på Elasticsearch 6.x.
exl-id: 60a423de-cf3a-4d73-a7cf-b6d9e95042ca
feature: Catalog Management, Categories, Search, Services
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Katalogsidindelning fungerar inte med Elasticsearch 6.x

I den här artikeln finns en patch för Adobe Commerce-problemet där katalogsidnumrering inte fungerar på Elasticsearch 6.x.

Korrigeringen nedan åtgärdar problem som användare av Adobe Commerce 2.3.3 har i distributioner där Elasticsearch 6.x används som katalogsökmotor. Användarna ser ett felmeddelande när de försöker navigera förbi den första sidan i sökresultaten.

När den här korrigeringen har installerats kan användarna bläddra igenom alla sökresultat.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur 2.3.3
* Adobe Commerce lokal 2.3.3
* Magento Open Source 2.3.3
* Elasticsearch 6.x

## Problem

Ett problem har upptäckts i Magento Open Source, Adobe Commerce lokalt och Adobe Commerce i molninfrastruktur där sidnumrering med sökresultat inte fungerar om du byter sida.

<u>Steg som ska återskapas</u>:

1. Installera Adobe Commerce.
1. Aktivera Elasticesach 6 som katalogsökmotor.
1. Lägg till ett antal produkter i kategorin som överskrider gränsen på en sida i Admin. **Anteckning**: 12 är standardantalet produkter som visas per sida i Adobe Commerce 2.3.3.
1. Öppna kategorin i butiken (antingen sökresultat eller kategorisida) och gå till sidan 2.

<u>Förväntat resultat</u>:

Produkterna ska visas på den andra sidan.

<u>Faktiskt resultat</u>:

**&quot;***Det går inte att hitta produkter som matchar markeringen***&quot;** -meddelandet visas på den andra sidan.

## Lösning

Åtgärda problemet genom att tillämpa den patch som är bifogad den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[Ladda ned katalogsidnumreringsproblem med Elasticsearch 6.x-korrigering](assets/Catalog_pagination_issue_on_Elasticsearch_6_composer-2019-10-11-08-07-41.patch.zip) - Korrigeringen är kompatibel med alla berörda versioner och utgåvor.

>[!WARNING]
>
>Adobe rekommenderar starkt att du sätter på plåstret så snart som möjligt, även om du inte har fått några symtom.

## Så här sätter du på plåstret

Se [Använda en kompositkorrigering från Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) för instruktioner.

## Bifogade filer
