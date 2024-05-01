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

I den här artikeln finns en fix för när huvudmenyn (eller [Navigeringsmeny för övre kategori](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) i vår användarhandbok) inte visas i butiken för undersidor (till exempel *blogg/sida*) när Fastly eller Varnish är aktiverat.

**Orsak:** det ej tillåtna `/` tecken (snedstreck) i *URL-nyckel* sidans parameter (Inställningar för sökmotoroptimering). Tecknet läggs vanligtvis till när *URL-sökväg* (med hela sidplatsen) anges av misstag i stället för *URL-nyckel*: till exempel *blogg/page\_name* i stället för bara *page\_name*.

**Lösning:** ta bort `/` tecken (snedstreck); för *URL-nyckel* anger du bara sidnamnet.

## Berörda versioner

* Adobe Commerce lokal 2.X.X
* Adobe Commerce i molninfrastruktur 2.X.X
* Fasta eller lack

## Problem

Huvudmenyn (kallas även [Navigeringsmeny för övre kategori](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) i vår användarhandbok) visas inte i butiken för undersidor när snabbast eller andra lack-baserade tjänster är aktiverade.

## Orsak

Problemet orsakas av det otillåtna `/` tecken (snedstreck), lägga till i *URL-nyckel* parameter (inställningar för sökmotoroptimering).

Tecknet läggs vanligtvis till när *URL-sökväg* (med hela sidplatsen, inklusive den överordnade resursen/katalogen för sidan) anges av misstag i stället för *URL-nyckel*: till exempel *blogg/page\_name* i stället för bara *page\_name*.

![URL-nyckelparameter för SEO-inställningar](assets/seo_url_key.png)

## Lösning

Ta bort `/` tecken (snedstreck) från *URL-nyckel* parameter för alla sidor i din butik.

Använd med andra ord *URL-nyckel* i stället för *URL-sökväg*: ange bara sidnamnet utan överordnad resurs/katalog.

### Recommendations i sidhierarki och SEO

Om du vill ange sidhierarkin använder du **Hierarki** på menyn Redigera sida.

![Inställningar för hierarki](assets/hierarchy_hr.png)

Du kan också använda **Innehåll** > **Element** > **Hierarki** -för mer komplexa hierarkilösningar.

För SEO-syften på produktsidor använder du URL-omskrivningar (**Marknadsföring** > **SEO &amp; Search** > **URL-omskrivning**).

## Mer information i vår användarhandbok

The *URL-nyckel* parameter för SEO:

* [Sökmotoroptimering](/docs/commerce-admin/catalog/categories/create/categories-search-engine-optimization.html)
* [Lägga till en ny sida](/docs/commerce-admin/content-design/elements/pages/page-add.html)

Sidhierarki:

* [Ökning](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html)
* [Lägga till en nod](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html#add-a-hierarchy-node)
