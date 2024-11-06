---
title: 'ACSD-45520: Alternativ för färgrutor har inte valts på produktinformationssidan'
description: Korrigeringen ACSD-45520 åtgärdar ett problem där alternativen för färgrutor inte är förvalda på produktinformationssidan när en användare redigerar konfigurerbara produkter från kundvagnen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 är installerat. Korrigerings-ID är ACSD-45520. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
exl-id: 941f4a45-bc3c-44c0-a582-ddfe179fa8c3
feature: Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-45520: Alternativ för färgrutor har inte valts på produktinformationssidan

Korrigeringen ACSD-45520 åtgärdar ett problem där alternativen för färgrutor inte är förvalda på produktinformationssidan när en användare redigerar konfigurerbara produkter från kundvagnen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 är installerat. Korrigerings-ID är ACSD-45520. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Alternativ för färgrutor väljs inte på produktinformationssidan när en användare redigerar konfigurerbara produkter från kundvagnen.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt med produktalternativ (till exempel färg).
1. Lägg den konfigurerbara produkten i kundvagnen.
1. Gå till sidan Min kundvagn.
1. Klicka på redigeringsknappen för den konfigurerbara produkt som lagts till i steg 1.
1. Lägg märke till produktalternativen på redigeringssidan.

<u>Förväntade resultat</u>:

Produktalternativ är valda.

<u>Faktiska resultat</u>:

Produktalternativ har inte valts.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i vår utvecklardokumentation.
