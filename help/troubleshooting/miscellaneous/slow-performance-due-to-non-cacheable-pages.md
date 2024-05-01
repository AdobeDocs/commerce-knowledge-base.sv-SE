---
title: Långsam prestanda på grund av icke-cachelagrade sidor
description: Den här artikeln innehåller lösningar för ökad inläsningstid för webbplatser eller avbrott på grund av att cache för hela sidor (t.ex. Fast) har inaktiverats för block på sidor som behöver cachas.
exl-id: 7401d9bd-710c-4221-9c3d-d78042c1c1ad
feature: Cache, Categories
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# Långsam prestanda på grund av icke-cachelagrade sidor

Den här artikeln innehåller lösningar för ökad inläsningstid för webbplatser eller avbrott på grund av att cache för hela sidor (t.ex. Fast) har inaktiverats för block på sidor som behöver cachas.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur 2.x.x
* Adobe Commerce lokal 2.x.x

### Problem

Webbplatsen har långsam prestanda eftersom det finns cacheblock på sidor som måste vara tillgängliga, men som har ställts in på `cacheable="false"` .

### Orsak

Det finns sidor som måste cachas av Adobe Commerce. De här sidorna har störst genomströmning. Varje begäran av den här typen av sidor som inte kommer från cachen gör att Adobe Commerce går långsammare.

Dessa sidor är:

* Katalogkategori (PLP)
* Produktinformationssida (PDP)
* Statiska innehållssidor (hemsida, kontakta oss, osv.)

Cacheable och uncacheable är termer som används för att ange om en sida ska cachelagras eller inte. Som standard är alla sidor tillgängliga. Om ett block i en layout däremot inte är tillgängligt är hela sidan inte tillgänglig.

Skärmbilden nedan visar ett block med en inställning `cacheable="false”`  ** ** som skapar en otillgänglig sida.

![non_cacheable_kb.png](assets/non_cacheable_kb.png)

Exempel på otillgängliga sidor är jämförelseprodukter, kundvagn och utcheckningssidor.

Följande lista med sidor cachelagras inte (cachelagring med fast, blockerad och layout undviks.) Detta inträffar på grund av layoutens cacheable-konfiguration.

### Lösning

Kontrollera om filerna som anges ovan har inställningen `cacheable="false”` . Om de har det, kontrollera om den här inställningen är nödvändig eller obligatorisk.

* Om det behövs kan du överväga att flytta icke-cachebara block till [mekanism för privat innehåll](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html?itm_source=devdocs&amp;itm_medium=quick_search&amp;itm_campaign=federated_search&amp;itm_term=private%20co) i stället.
* Ta bort attributet om det inte behövs `cacheable="false”` och tömma layoutcachen.

>[!NOTE]
>
>För Adobe Commerce i molninfrastruktur 2.4.1 och senare kan du använda [Site-Wide Analysis Tool](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) för att automatiskt kontrollera om helsidescachen inte är korrekt konfigurerad.

### Relaterad läsning

[Översikt över Adobe Commerce cache](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/cache_for_frontdevs.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=cacheable%2) i vår dokumentation för utvecklare.
