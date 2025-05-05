---
title: "MDVA-40399: Det går inte att skapa partiella fakturor för samma order samtidigt via API"
description: Korrigeringen MDVA-40399 åtgärdar ett problem där partiella fakturor för samma order inte kan skapas samtidigt via Rest API. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 är installerat. Korrigerings-ID är MDVA-40399. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
exl-id: 2444ba57-b30b-4fdf-9e5d-988cf7fa8dd1
feature: REST, Invoices, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# MDVA-40399: Det går inte att skapa partiella fakturor för samma order samtidigt via API

Korrigeringen MDVA-40399 åtgärdar ett problem där partiella fakturor för samma order inte kan skapas samtidigt via Rest API. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 har installerats. Korrigerings-ID är MDVA-40399. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det går inte att skapa partiella fakturor för samma order samtidigt med Rest API.

<u>Förutsättningar</u>:

En konfigurerbar produkt med minst två variationer.

<u>Steg som ska återskapas</u>:

1. Lägg båda varianterna av den konfigurerbara produkten i kundvagnen.
1. Beställ.
1. Skapa två fakturor samtidigt för ordern via Rest API.

<u>Förväntade resultat</u>:

* Båda fakturorna måste skapas.
* `qty_invoiced` ska uppdateras för båda fakturorna i tabellen `sales_order_item`.
* Båda produkterna ska ha fakturerad kvantitet.

<u>Faktiska resultat</u>:

* Båda fakturorna har skapats.
* `qty_invoiced` uppdateras inte mot en av fakturorna i tabellen `sales_order_item`.
* Fakturakvantiteten visas endast för en produkt på sidan **Ordervy** hos administratören.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
