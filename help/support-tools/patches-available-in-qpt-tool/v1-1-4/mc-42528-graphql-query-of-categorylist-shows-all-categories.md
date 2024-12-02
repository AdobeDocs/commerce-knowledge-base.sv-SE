---
title: 'MC-42528: GraphQL-frågan för categoryList visar alla kategorier'
description: Korrigeringen MC-42528 löser problemet där GraphQL-frågan för categoryList returnerar både tilldelade och ej tilldelade kategorier när bläddringskategorin för en viss kategori är inställd på Neka. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 är installerat. Korrigerings-ID är MC-42528. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: 8bb29f43-92ae-4f37-b147-7121b55c185b
feature: Catalog Management, Categories, GraphQL, Customer Service
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MC-42528: GraphQL-frågan för categoryList visar alla kategorier

Korrigeringen MC-42528 löser problemet där GraphQL-frågan `categoryList` returnerar både tilldelade och ej tilldelade kategorier när bläddringskategorin för en viss kategori är inställd på&quot;Neka&quot;. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 har installerats. Korrigerings-ID är MC-42528. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

GraphQL-frågan för `categoryList` returnerar både tilldelade och ej tilldelade kategorier.

<u>Steg som ska återskapas</u>:

1. Skapa två kategorier, CAT1 och CAT2, och tilldela ett fåtal produkter till varje kategori.
1. Skapa en privat delad katalog.
1. Skapa en företagsanvändare och tilldela den till den skapade delade katalogen.
1. Tilldela CAT1 till den anpassade katalogen och ange kategoribehörigheten till&quot;Tillåt&quot; bläddringskategori för kundgruppen i den privata katalogen.
1. Ställ in kategoribehörigheten för CAT2 på bläddringskategorin&quot;Neka&quot; för kundgruppen för den privata katalogen.
1. Kör `categoryList`- eller `categories` GraphQL-frågan som företagsanvändare.

<u>Förväntade resultat</u>:

Endast CAT1 visas i svaret.

<u>Faktiska resultat</u>:

Alla kategorier visas i svaret oavsett kategoriens bläddringsbehörigheter.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
