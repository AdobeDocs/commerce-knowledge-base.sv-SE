---
title: 'MDVA-40488: Konfigurerbara produkter med underordnade produkter utanför lagret visas inte i rätt prisintervall'
description: MDVA-40488-korrigeringen åtgärdar ett problem där konfigurerbara produkter med underordnade produkter utanför lagret inte visas i rätt prisintervall. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 är installerat. Korrigerings-ID är MDVA-40488. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: 0c4b9f5e-ae41-409e-b244-1d7cf948ed6f
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# MDVA-40488: Konfigurerbara produkter med underordnade produkter utanför lagret visas inte i rätt prisintervall

MDVA-40488-korrigeringen åtgärdar ett problem där konfigurerbara produkter med underordnade produkter utanför lagret inte visas i rätt prisintervall. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 har installerats. Korrigerings-ID är MDVA-40488. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Konfigurerbara produkter med underordnade produkter som inte finns i lager visas inte i rätt prisintervall.

<u>Förutsättningar</u>:

Gå till Commerce Admin > **stores** > **configuration** > **catalog** > **Inventory** > **stock options** och ställ in **Display Out of Stock Products** -konfigurationen på *Yes*.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt med två associerade produkter. Till exempel: enkla produkter Red och Brown.
1. Ange lagret för den enkla produkten Red och ange Stock-status till *I Stock*, och ange sedan statusen Enable Product (Aktivera produkt) till *No*.
1. Ställ in lager för den enkla produkten Brown och ställ sedan in statusen Enable Product (Aktivera produkt) på *Yes*.
1. Kontrollera att den konfigurerbara produktStock-statusen är *I Stock*.
1. Ändra lagret för den enkla produkten Brown till 0 och ange Stock-statusen till *Utanför lager*.
1. För närvarande är den konfigurerbara produktStock-statusen fortfarande *I Stock*.
1. Utför omindexering.
1. Kontrollera `min_price` och `max_price` för den konfigurerbara produkten i databastabellen `catalog_product_index_price` - de två värdena är inställda på 0.
1. Men om vi ställer in den konfigurerbara produktStock-statusen till *Utanför lager* och indexerar om, kan vi se värden som inte är noll `min_price` och `max_price` för den konfigurerbara produkten.

<u>Förväntade resultat</u>:

Om alla underordnade produkter är *Utanför Stock* och den konfigurerbara produkten också är *Utanför Stock* beräknas priset med hjälp av alla underordnade produkter.

<u>Faktiska resultat</u>:

`min_price`- och `max_price`-värdena för den konfigurerbara produkten i `catalog_product_index_price` DB-tabellen anges till 0 när den konfigurerbara Stock-statusen är *I lager*, men om den är *Utanför lager* blir de inte nollvärden.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i vår utvecklardokumentation.
