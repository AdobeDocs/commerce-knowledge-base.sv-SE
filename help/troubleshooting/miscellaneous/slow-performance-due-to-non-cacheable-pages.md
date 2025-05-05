---
title: Långsam prestanda på grund av icke-cachelagrade sidor
description: Den här artikeln innehåller lösningar för ökad inläsningstid för webbplatser eller avbrott på grund av att cache för hela sidor (t.ex. Fast) har inaktiverats för block på sidor som behöver cachas.
exl-id: 7401d9bd-710c-4221-9c3d-d78042c1c1ad
feature: Cache, Categories
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Webbplatsen har långsam prestanda eftersom det finns cacheblock på sidor som måste vara tillgängliga men som har angetts till `cacheable="false"`.

### Orsak

Det finns sidor som måste cachas av Adobe Commerce. De här sidorna har störst genomströmning. Varje begäran av den här typen av sidor som inte kommer från cachen gör att Adobe Commerce går långsammare.

Dessa sidor är:

* Katalogkategori (PLP)
* Produktinformationssida (PDP)
* Statiska innehållssidor (hemsida, kontakta oss, osv.)

Cacheable och uncacheable är termer som används för att ange om en sida ska cachelagras eller inte. Som standard är alla sidor tillgängliga. Om ett block i en layout däremot inte är tillgängligt är hela sidan inte tillgänglig.

Skärmbilden nedan visar ett block med inställningen `cacheable="false"` **&#x200B; ** som skapar en otillgänglig sida.

![non_cacheable_kb.png](assets/non_cacheable_kb.png)

Exempel på otillgängliga sidor är jämförelseprodukter, kundvagn och utcheckningssidor.

Följande lista med sidor cachelagras inte (cachelagring med fast, blockerad och layout undviks.) Detta inträffar på grund av layoutens cacheable-konfiguration.

### Lösning

Kontrollera om filerna som anges ovan har inställningen `cacheable="false"`. Om de har det, kontrollera om den här inställningen är nödvändig eller obligatorisk.

* Om det behövs kan du överväga att flytta icke-cachebara block till [mekanismen för privat innehåll](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) i stället.
* Om det inte behövs tar du bort attributet `cacheable="false"` och tömmer layoutcachen.

>[!NOTE]
>
>För Adobe Commerce i molninfrastruktur 2.4.1 och senare kan du använda [Site-Wide Analysis Tool](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/site-wide-analysis-tool/access) för att automatiskt kontrollera om helsidescachen inte är korrekt konfigurerad.

### Relaterad läsning

[Översikt över Adobe Commerce-cache](https://developer.adobe.com/commerce/frontend-core/guide/caching/) i utvecklardokumentationen.
