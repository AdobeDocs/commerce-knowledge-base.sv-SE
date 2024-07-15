---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.0.7'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.0.7.
exl-id: 2415ca7a-4aec-4a63-9ae9-ee7b29bbc8d7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.7 - översikt

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i [!DNL Quality Patches Tool] (QPT) v1.0.7.

QPT v1.0.7 innehåller följande patchar:

1. **MDVA-29148**: Korrigerar problemet när en produkt skapas via ett API-anrop. Det anpassade produktattributet `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (som Multiselect) använder inte standardvärdet om inget värde angavs i nyttolasten.
1. **MDVA-29389**: Korrigerar problemet med avancerad rapportering där `analytics_collect_data` cronjob säger: *Port måste konfigureras i värdparametern (som localhost:3306)*.
1. **MDVA-30594**: Korrigerar problemet där en order med flera adresser inte kunde sparas vid utcheckning när FPT har konfigurerats.
1. **MDVA-30782**: Korrigerar problemet där dynamiskt block visas oavsett kundvagnsregel.
1. **MDVA-30815**: Korrigerar problemet där du ändrar hur många sökresultat som ska visas på sökresultatsidan.
1. **MDVA-30837**: Lägger till konfigurationsalternativ för beräkning av fri frakt så att användaren kan konfigurera minimiorderbeloppet för fri frakt baserat på delsumman (eller totalsumman).
1. **MDVA-30945**: Korrigerar problemet där du får ett allvarligt felmeddelande när du uppdaterar kundvagnen `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.
1. **MDVA-30972**: Korrigerar problemet där status för anpassad order ändrades till *Bearbetning* efter att en del av leveransen skapats med WebApi.
1. **MDVA-31007**: Korrigerar problemet där anpassade adressattribut inte visas korrekt på sidan med orderinformation i mitt kontoområde och i serverdelen.
1. **MDVA-31021**: Korrigerar problemet där prestandaproblem förekommer i `module-catalog-import-export/Model/Import/Product/Option.php`. Om det finns fler än ~100 kB poster i tabellen `catalog_product_option` tar det mindre än 10 sekunder att validera en ny CSV med en enskild produkt.
1. **MDVA-31224**: Förbättrar prestandan för omindexeringsåtgärden `catalog_product_price` för paketprodukter.
1. **MDVA-31282**: Korrigerar ett problem där dubbla auktoriseringar förekommer på [!DNL Paypal PayFlow Pro] i Adobe Commerce. Dubbla auktoriseringar innebär också att [!DNL PayFlow Pro's]-bedrägerifilter ignoreras och transaktionsavgifter dubbleras.
1. **MDVA-31343**: Korrigerar problemet med den borttagna brödklassen `page-layout-category-full-width` när en kategori är schemalagd.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
