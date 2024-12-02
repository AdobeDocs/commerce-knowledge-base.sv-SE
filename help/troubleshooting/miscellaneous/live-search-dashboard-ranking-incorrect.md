---
title: Instrumentpanelen [!DNL Live Search] och rankningen av sökresultat är felaktig
description: I den här artikeln finns felsökningsinformation om data i  [!DNL Live Search] kontrollpanelen är felaktiga eller om rangordningen av sökresultaten inte är vad du förväntar dig.
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: d4aea1f1-c2c4-45e5-87c8-73069f7c9ffd
source-git-commit: 9bb839292a120a3dab5151d493f915619dbf5c06
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
