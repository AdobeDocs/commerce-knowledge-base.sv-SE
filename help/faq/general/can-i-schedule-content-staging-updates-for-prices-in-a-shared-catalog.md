---
title: Kan jag schemalägga Content Staging-uppdateringar för priser i en delad katalog?
description: Adobe Commerce erbjuder inte möjligheten att schemalägga en prisuppdatering ([Content Staging](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html)) för en eller flera produkter i en delad katalog.
exl-id: 5482326f-54c2-4efc-8e5e-6d075ee5be55
feature: Catalog Management, Customer Service
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Kan jag schemalägga Content Staging-uppdateringar för priser i en delad katalog?

Adobe Commerce erbjuder inte möjligheten att schemalägga en prisuppdatering ([Innehållsmellanlagring](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html)) för en eller flera produkter i en delad katalog.

Det innebär att du inte kan schemalägga en sådan prisuppdatering direkt från **Ange priser och struktur** menyn på Commerce Admin-panelen (det finns ingen **Schemalägg ny uppdatering** på den här menyn).

Du kan ändå använda alternativa metoder och schemalägga en prisuppdatering för:

* en kundgrupp
* produktens baspris

## Schemalägg prisuppdatering för en kundgrupp

1. Starta [planera en ny produktuppdatering](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html).
1. Bläddra nedåt till **Pris** fält och klicka **Avancerade priser**.

   ![advanced_pricing.png](assets/advanced_pricing.png){width="600"}

1. I **Kundgruppprissektion** väljer du kundgrupp och anger det uppdaterade priset.

   ![customer_group_price.png](assets/customer_group_price.png){width="700"}

1. Slutför schemaläggningen av uppdateringen som vanligt.

I det här arbetsflödet kan du bara uppdatera priset för en enskild produkt. Det går inte att uppdatera bulkpriset.

Kom ihåg: delade kataloger utnyttjar kundens grupppriser.

**Relaterad dokumentation**

* [Schemalägga en uppdatering (Content Staging)](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html) i vår användarhandbok.
* [Avancerade priser](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) i vår användarhandbok.

## Schemalägg prisuppdatering för baspriset

Se artikeln: [Hur basprisändringen påverkar priset på den delade katalogen?](/help/faq/general/base-price-change-affect-on-shared-catalog-price.md) i vår kunskapsbas för support.
