---
title: 'ACSD-45488: Konfigurerbar produkt med flera källor som inte returneras till i lager automatiskt'
description: Korrigeringen ACSD-45488 löser problemet där en konfigurerbar produkt med flera källor inte returneras till i lager automatiskt. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 är installerat. Korrigerings-ID är ACSD-45488. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
exl-id: 83332226-b14e-4d36-bf65-170f55fff270
feature: Configuration, Orders, Products, Returns
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# ACSD-45488: Konfigurerbar produkt med flera källor som inte returneras till i lager automatiskt

Korrigeringen ACSD-45488 löser problemet där en konfigurerbar produkt med flera källor inte returneras till i lager automatiskt. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 är installerat. Korrigerings-ID är ACSD-45488. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En konfigurerbar produkt med flera källor returneras inte automatiskt till i lager.

<u>Steg som ska återskapas</u>:

1. Skapa en sekundär Stock-källa.
1. Skapa en konfigurerbar produkt med två associerade virtuella produkter.
1. Tilldela de associerade produkterna till standardlagerkällan och ange kvantiteten till en.
1. Kontrollera `stock_status` från `cataloginventory_stock_status`.
1. Ange att båda de associerade produkterna ska vara *utanför lagret*.
1. Kontrollera `stock_status` från `cataloginventory_stock_status`.
1. Ange att båda associerade produkter ska vara *i lager*.
1. Kontrollera `stock_status` från `cataloginventory_stock_status`.

<u>Förväntade resultat</u>:

Lagerstatusen för den konfigurerbara produkten uppdateras till *i lager* när de associerade produkterna är i lager.

<u>Faktiska resultat</u>:

Lagerstatusen för den konfigurerbara produkten uppdateras inte till *i lager* när de associerade produkterna är i lager.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i vår utvecklardokumentation.
