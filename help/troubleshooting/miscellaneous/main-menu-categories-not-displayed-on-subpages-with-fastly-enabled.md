---
title: Huvudmeny (kategorier) visas inte på undersidor med snabbaktiverad
description: I den här artikeln finns en fix som anger när huvudmenyn (eller menyn [Kategori > navigering](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) i användarhandboken) inte visas på butiken för undersidor (till exempel *blog/page*) när Fastly eller Varnish är aktiverat.
exl-id: 7c54791d-8aa6-4f01-a28b-a7aecdb8ff74
feature: Categories, Marketing Tools
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Huvudmeny (kategorier) visas inte på undersidor med snabbaktiverad

I den här artikeln finns en korrigering för när huvudmenyn (eller menyn [Övre kategorinavigering](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) i användarhandboken) inte visas på butiken för undersidor (till exempel *blogg/sida*) när Snabbt eller Slutför är aktiverat.

**Orsak:** det otillåtna `/`-tecknet (snedstreck) i parametern *URL-nyckel* på sidan (inställningar för sökmotoroptimering). Tecknet läggs vanligtvis till när *URL-sökvägen* (med hela sidplatsen) av misstag anges i stället för *URL-nyckeln*: till exempel *blog/page\_name* i stället för bara *page\_name*.

**Lösning:** ta bort tecknet `/` (snedstreck); för parametern *URL-nyckel* anger du bara sidnamnet.

## Berörda versioner

* Adobe Commerce lokal 2.X.X
* Adobe Commerce i molninfrastruktur 2.X.X
* Fasta eller lack

## Problem

Huvudmenyn (kallas även [Övre navigeringsmeny för kategori](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) i användarhandboken) visas inte i butiken för undersidor när Fastly eller andra Varnish-baserade tjänster är aktiverade.

## Orsak

Problemet orsakas av det otillåtna `/`-tecknet (snedstreck) som läggs till i parametern *URL-nyckel* (inställningar för sökmotoroptimering).

Tecknet läggs vanligtvis till när *URL-sökvägen* (med hela sidplatsen, inklusive sidans överordnade resurs/katalog) felaktigt anges i stället för *URL-nyckeln*: till exempel *blogg/sida\_name* i stället för bara *sida\_name*.

![URL-nyckelparameter för SEO-inställningar](assets/seo_url_key.png)

## Lösning

Ta bort tecknet `/` (snedstreck) från parametern *URL-nyckel* för alla sidor i din butik.

Använd med andra ord *URL-nyckel* i stället för *URL-sökväg*: ange bara sidnamnet utan överordnad resurs/katalog.

### Recommendations i sidhierarki och SEO

Om du vill ange sidhierarkin använder du avsnittet **Hierarki** på menyn Redigera sida.

![Hierarkiinställningar](assets/hierarchy_hr.png)

Du kan också använda menyn **Innehåll** > **Element** > **Hierarki** för mer komplexa hierarkilösningar.

Använd URL-omskrivningar för SEO-syften på produktsidor (**Marknadsföring** > **SEO &amp; sökning** > **URL-omskrivningar**).

## Mer information i vår användarhandbok

Parametern *URL-nyckel* för SEO:

* [Sökmotoroptimering](/docs/commerce-admin/catalog/categories/create/categories-search-engine-optimization.html)
* [Lägga till en ny sida](/docs/commerce-admin/content-design/elements/pages/page-add.html)

Sidhierarki:

* [Ökning](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html)
* [Lägga till en nod](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html#add-a-hierarchy-node)
