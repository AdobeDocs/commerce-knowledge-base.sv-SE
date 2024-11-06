---
title: 'ACSD-45169: Visual Merchandiser visar felaktigt lager och pris för konfigurerbar produkt'
description: Korrigeringsfilen ACSD-45169 åtgärdar ett problem där Visual Merchandiser inte visar rätt lager och pris för en konfigurerbar produkt efter att en mellanlagringsuppdatering har tillämpats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 är installerat. Korrigerings-ID är ACSD-45169. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
exl-id: 5a7987c8-f276-4917-98f7-645402f4c454
feature: Categories, Configuration, Merchandising, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# ACSD-45169: Visual Merchandiser visar felaktigt lager och pris för konfigurerbar produkt

Korrigeringsfilen ACSD-45169 åtgärdar ett problem där Visual Merchandiser inte visar rätt lager och pris för en konfigurerbar produkt efter att en mellanlagringsuppdatering har tillämpats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 är installerat. Korrigerings-ID är ACSD-45169. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Visual Merchandiser visar inte korrekt aktie och pris för en konfigurerbar produkt efter att en mellanlagringsuppdatering har tillämpats.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt.
1. Skapa alla schemalagda uppdateringar för den enkla produkten (du behöver bara ha olika rad- och enhets-ID).
1. Skapa en konfigurerbar produkt.
1. Tilldela den konfigurerbara produkten till en kategori.
1. Öppna kategorin och observera den konfigurerbara produkten under Visual Merchandiser-sektionen.

<u>Förväntade resultat</u>:

Visual Merchandiser visar rätt aktie och pris.

<u>Faktiska resultat</u>:

Visual Merchandiser visar en felaktig aktie och ett felaktigt pris.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i vår utvecklardokumentation.
