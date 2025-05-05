---
title: Uppdateringar av schemalagd förproduktion av innehåll visas inte med snabb inlagring
description: I den här artikeln finns en korrigering för när Adobe Commerce butiker inte visar schemalagda uppdateringar när Content Staging och Fast används. Problemet beror på att Snabbt mjuk tömning är aktiverat som standard. Den här funktionen minskar belastningen på programresurser och återskapar bara en ny cache vid en andra begäran. För att lösa problemet kan du aktivera Rensa CMS-sidan via Commerce Admin för att alltid generera om och leverera nytt innehåll.
exl-id: becbffaa-b6dd-4e9b-894e-17901c40223a
feature: CMS, Cache, Page Content, Staging
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# Uppdateringar av schemalagd förproduktion av innehåll visas inte med snabb inlagring

I den här artikeln finns en korrigering för när Adobe Commerce butiker inte visar schemalagda uppdateringar när Content Staging och Fast används. Problemet beror på att Snabbt mjuk tömning är aktiverat som standard. Den här funktionen minskar belastningen på programresurser och återskapar bara en ny cache vid en andra begäran. För att lösa problemet kan du aktivera Rensa CMS-sidan via Commerce Admin för att alltid generera om och leverera nytt innehåll.

## Problem

Schemalagda uppdateringar för en butiksinnehållsresurs (sida, produkt, block osv.) visas inte i butiken omedelbart efter uppdateringens starttid. Det här inträffar när uppdateringar har schemalagts med funktionen [Innehållsmellanlagring](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html?lang=sv-SE).

## Orsak

På grund av Fastlyys funktion för mjuk tömning (aktiverad som standard) får Adobe Commerce storefront fortfarande det gamla (inaktuella) cachelagrade innehållet när **den första**-begäran för den uppdaterade resursen skickas till Snabbt. Kräver snabbt en andra begäran för att återskapa webbplatsdata.

Det innebär att Fastly kan leverera gammalt innehåll fram till den andra begäran om det uppdaterade innehållet.

**Cachelagring förväntades:** När vi har schemalagt en uppdatering för en innehållsresurs med hjälp av Content Staging skickar Adobe Commerce en begäran om att uppdatera cachen till Fast. Gör det tidigare cachelagrade innehållet ogiltigt (utan att innehållet tas bort) och börjar bearbeta det uppdaterade innehållet.

**Faktisk cachelagring:** Om det inaktuella innehållet fortfarande visas när **den första**-begäran för det uppdaterade innehållet tas emot, skickas återskapat innehåll endast efter att **den andra**-begäran har tagits emot. Det här beteendet har implementerats för att minska serverbelastningen genom att cachen endast förnyas i områden med beprövad trafik, utan att cachen genereras om för hela webbplatsen. Uppdaterar snabbt cacheminnet gradvis och sparar programresurserna.

## Lösning

Om det inte går att skicka gammalt innehåll även för den första begäran kan du inaktivera Mjuk tömning och aktivera Rensa CMS-sida:

1. Logga in som administratör hos din lokala Commerce-administratör.
1. Gå till **Lagrar** > **Konfiguration** > **Avancerat** > **System** > **Helsidescache**.
1. Expandera **Snabb konfiguration** och expandera sedan **Avancerat**.
1. Ange **Använd mjuk rensning** till *Nej*.
1. Ange **Rensa CMS-sida** till *Ja*.
1. Klicka på **Spara konfiguration** överst på sidan.


![purge_options.png](assets/purge_options.png)

## Relaterad dokumentation

* [Konfigurera rensningsalternativ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=sv-SE) i infrastrukturguiden för Commerce i molnet.
* [Förproduktion av innehåll](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html?lang=sv-SE) i dokumentationen för innehåll och design.
* [Skickar inaktuellt innehåll](https://docs.fastly.com/guides/performance-tuning/serving-stale-content) i Snabbdokumentation.
