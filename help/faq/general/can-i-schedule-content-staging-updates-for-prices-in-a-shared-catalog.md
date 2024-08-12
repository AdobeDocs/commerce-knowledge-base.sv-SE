---
title: Kan jag schemalägga Content Staging-uppdateringar för priser i en delad katalog?
description: Adobe Commerce erbjuder inte möjligheten att schemalägga en prisuppdatering ([Content Staging](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html)) för en eller flera produkter i en delad katalog.
exl-id: 5482326f-54c2-4efc-8e5e-6d075ee5be55
feature: Catalog Management, Customer Service
source-git-commit: c3120f7df24e105b082df6544ab82241d6b6851f
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# Kan jag schemalägga Content Staging-uppdateringar för priser i en delad katalog?

Adobe Commerce erbjuder inte funktioner för att schemalägga en prisuppdatering ([Content Staging](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html)) för en eller flera produkter i en delad katalog.

Det innebär att du inte kan schemalägga en sådan prisuppdatering direkt från menyn **Ange priser och struktur** på Commerce Admin-panelen (det finns ingen **Schemalägg ny uppdatering** på den här menyn).

Du kan ändå använda alternativa metoder och schemalägga en prisuppdatering för:

* en kundgrupp
* produktens baspris

## Schemalägg prisuppdatering för en kundgrupp

1. Starta [schemaläggningen av en ny produktuppdatering](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html).
1. Bläddra ned till fältet **Pris** och klicka på **Avancerade priser**.

   ![advanced_pricing.png](assets/advanced_pricing.png){width="600"}

1. I avsnittet **Kundgruppspris** väljer du önskad kundgrupp och anger det uppdaterade priset.

   ![customer_group_price.png](assets/customer_group_price.png){width="700"}

1. Slutför schemaläggningen av uppdateringen som vanligt.

I det här arbetsflödet kan du bara uppdatera priset för en enskild produkt. Det går inte att uppdatera bulkpriset.

Kom ihåg: delade kataloger utnyttjar kundens grupppriser.

**Relaterad dokumentation**

* [Schemalägger en uppdatering (Content Staging)](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html) i användarhandboken.
* [Avancerade priser](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) i användarhandboken.

## Schemalägg prisuppdatering för baspriset

Se den relaterade artikeln: [Hur basprisändringen påverkar priset på den delade katalogen?](/help/faq/general/base-price-change-affect-on-shared-catalog-price.md) i vår kunskapsbas för support.
