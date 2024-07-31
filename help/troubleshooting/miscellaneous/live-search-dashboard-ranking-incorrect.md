---
title: Instrumentpanelen [!DNL Live Search] och rankningen av sökresultatet är felaktig
description: I den här artikeln finns felsökningsinformation om data i  [!DNL Live Search] kontrollpanelen är felaktiga eller om rangordningen av sökresultaten inte är vad du förväntar dig.
feature: Admin Workspace, Categories, Search
role: Developer
source-git-commit: 4c1199c31f83d7c2aaf28e259d63473779bf2efe
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---

# Instrumentpanelen [!DNL Live Search] och rankningen av sökresultat är felaktig

Om du observerar att de data som visas på kontrollpanelen [!DNL Live Search] är felaktiga eller om [rankningen av sökresultaten](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/category-merch#ranking-strategies) inte är vad du förväntar dig, kan du läsa följande av möjliga orsaker:

* Fältet `topLevelSku` i produktkontexten i `productView`-händelser saknas. Detta orsakar tomma konverteringar och andra oväntade mätvärden.

* Händelsen `add-to-cart` har inte fältet `productContext` inställt och ifyllt.

* Miljötypen är felaktig. Om miljön till exempel är inställd på *[!UICONTROL Testing]* i stället för *[!UICONTROL Production]*. Mer information finns i [StoreFront-kontext](https://github.com/adobe/commerce-events/blob/main/examples/events/example-contexts/mock-storefront-context.md).

* Sökresultatkontexten saknas i [sökproduktklickhändelsen ](https://github.com/adobe/commerce-events/blob/main/examples/events/search-product-click.md).
