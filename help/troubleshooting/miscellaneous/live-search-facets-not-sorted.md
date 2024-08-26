---
title: '[!DNL Live Search] facets sorteras inte i alfabetisk ordning'
description: Den här artikeln innehåller felsökningsinformation om  [!DNL Live Search] facets inte är sorterat i bokstavsordning.
feature: Admin Workspace, Categories, Search
role: Developer
source-git-commit: 5387edb46281fc536402f8ce0a5e2a77c1bd4193
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# [!DNL Live Search] facets sorteras inte i alfabetisk ordning

## Berörda produkter och versioner

Adobe Commerce version 2.4.x och senare

Alla Adobe Commerce storefront-ansikten sorteras i bokstavsordning med alternativ för en enstaka markering, oavsett vilken indatatyp som tilldelats motsvarande attribut.

I vissa kantfall kanske inte ansiktena sorteras i alfabetisk ordning enligt inställningarna i [[!DNL Live Search] Motstående arbetsyta](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/facets/faceting-workspace). Som en tillfällig lösning kan du sortera produktattribut i avsnittet [!UICONTROL Admin]-attribut.

1. Gå till **Lager** > *Attribut* > **Produkt** i sidofältet **[!UICONTROL Admin]**.
1. Markera ett attribut i tabellen.

   ![Attributlista](assets/attribute-list.png)

1. Öppna attributet som har de värden som du vill sortera och välj **Attributinformation** > **Egenskaper**.
1. Under **Hantera alternativ** kan du sortera attributvärdena.

   ![Sorteringsattribut](assets/sort-attributes.png)
